<script setup>
///variables 
const character = defineProps([
  "name",
  "status",
  "species",
  "image",
  "loading"
])
</script>


<template>
  <div class="card text-light mb-3 card border-light detailCard" :class="loading ? 'animate__animated animate__flipInX' : ''">
    <img v-if="character.name" :src="character.image" alt="Character Image" class="card-img-top img-fluid">

    <img  v-else src="../assets/interrogation.svg" alt="???" class="card-img-top img-fluid">

    <div class="card-body">
      <h5 class="card-title text-center">{{ character.name || "???"}}</h5>
      <hr>
      <div class="row">
        <section class="col">
          <strong>Status:</strong>
          <span>{{ character.status }}</span>
        </section> <!--col-->

        <section class="col">
          <strong>Species:</strong>
          <span>{{ character.species }}</span>
        </section> <!--col-->
      </div> <!--row-->
    </div> <!--card body-->
  </div> <!--card-->
</template>

<style scoped>
.detailCard {
  background: linear-gradient(90deg, #43A047, #90CAF9);  
  border-radius: 8px;
  padding: 10px;
  box-shadow: 0px 2px 6px rgba(0, 0, 0, 0.1);
  height: 75vh;
}

.card-title {
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 10px;
}

.row {
  display: flex;
  justify-content: space-between;
  margin-top: 10px;
}

.col {
  flex-basis: 45%;
}

strong {
  font-weight: bold;
  margin-right: 5px;
}

@media (max-width: 576px) {
  .col {
    flex-basis: 100%;
    margin-top: 10px;
  }
}
</style>
