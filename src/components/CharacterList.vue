<script setup>
// We will work with props for the component to be ready to receive the data
const character = defineProps([
  "name", "charactersURL"
])
</script>


<template>
  <div class="col-12 col-sm-6 col-md-4 col-lg-3 mb-3">
    <div class="card rickAndMortyCard">
      <img :src="charactersURL" class="card-img-top img-fluid" alt="Character Image">
      <div class="card-body">
        <p class="card-title text-center">{{ name }}</p>
      </div> <!--card-body-->
    </div> <!--card-->
  </div> <!--col-->
</template>

<style scoped>
.rickAndMortyCard {
  position: relative;
  cursor: pointer;
  background: #555;
  overflow: hidden;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.card-img-top {
  height: 200px;  
  object-fit: cover;
}

.card-body {
  padding: 10px;
}

.card-title {
  font-size: 16px;
  font-weight: bold;
  margin-bottom: 0;
  color: #fff;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
}

@media (max-width: 576px) {
  .col-12 {
    flex-basis: 100%;
    max-width: 100%;
  }

  .card-img-top {
    height: 150px; 
  }

  .card-title {
    font-size: 14px; 
  }
}
</style>
