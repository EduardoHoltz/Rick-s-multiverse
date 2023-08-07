<script setup>
///imports 
import { onMounted, ref, computed, reactive } from "vue"
import CharacterList from "../components/CharacterList.vue"
import CharacterSelectedVue from "../components/CharacterSelected.vue"

///variables
let characters = ref([])
let searchCharacter = ref("")
let selected = reactive(ref())
let loading = ref(false)

///select and show the info about some character
const selectedCharacter = async (character) => {
  loading.value = true
  await fetch(character.url)
    .then((res) => res.json())
    .then((data) => { selected.value = data })
    .catch((err => alert(err)))
    .finally(() => {
      loading.value = false
    })
}

/// basically going to get chars in api  
onMounted(async () => {

  ///filter to get characters
  const page = 1
  const perPage = 1
  const url = `https://rickandmortyapi.com/api/character/?page=${page}&perPage=${perPage}`;

  /*
  - fetch() returns a Promise, so i use then() and response to get with json()
  - json() returns a Promise too, so i use then() again 
  - data is what i want to show 
  */
  fetch(url)
    .then((res) => res.json())
    .then((data) => { characters.value = data.results })
})

/// searching a character by filter and input 
const filteredCharacters = computed(() => {
  if (characters.value && searchCharacter.value) {
    return characters.value.filter(character => character.name.toLowerCase().includes(searchCharacter.value.toLowerCase()))
  }
  return characters.value
})

/// the rick and morty api has a image field, so i can return the image by 'index'.image
function getCharacterImageUrl(character) {
  return character.image
}
</script>

<template>
  <main>
    <div class="container">
      <div class="row mt-5">

        <!-- SELECTED CHARACTER CARD -->
        <div class="col-12 col-md-6 col-lg-4">
          <!-- === CharacterSelectedVue === -->
          <CharacterSelectedVue :name="selected?.name ?? ''" :status="selected?.status ?? ''"
            :species="selected?.species ?? ''" :image="selected?.image ?? ''" :loading="loading">
          </CharacterSelectedVue>
          <!-- === CharacterSelectedVue === -->
        </div><!--col-->

        <!-- LIST OF CHARACTER -->
        <div class="col-12 col-md-6 col-lg-8">
          <div class="card card-list text-bg-secondary mb-3 card border-dark">
            <div class="card-body row">
              <div class="input-group mb-3">
                <label hidden for="Search" class="form-label">Search</label>
                <input v-model="searchCharacter" type="text" class="form-control" id="Search" placeholder="Search . . ."
                  aria-label="Search" aria-describedby="basic-addon1">
              </div> <!--input-->
              <!-- === CharacterList === -->
              <CharacterList v-for="(character, index) in filteredCharacters" :key="index" :name="character.name"
                :charactersURL="getCharacterImageUrl(character)" @click="selectedCharacter(character)">
              </CharacterList>
              <!-- === CharacterList === -->
            </div> <!--card body-->
          </div> <!--card-->
        </div><!--col-->
      </div><!--row-->
    </div> <!--container-->
  </main>
</template>

<style scoped>
main {
  background: linear-gradient(90deg, #43A047, #90CAF9);
  min-height: 100vh;
  padding-top: 20px;
}

.card-list {
  overflow-y: scroll;
  overflow-x: hidden;
  max-height: 75vh;
}

.input-group {
  width: 100%;
}

.form-control {
  border-radius: 8px;
  background-color: #fff; 
  color: #555; 
  font-size: 16px;
}

.form-control::placeholder {
  color: #888;  
}

.input-group-append {
  margin-left: -36px;
}

.input-group-text {
  background-color: #43A047;  
  border: none;
  color: #fff; 
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.input-group-text:hover {
  background-color: #2E7D32; 
}
</style>
