<script setup>
</script>

<template>
  <!-- menu -->
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark border-bottom border-body">
    <div class="container">
      <router-link class="navbar-brand" to="/">
        <img src="./assets/rick.svg" alt="logo" width="30" height="24">
      </router-link>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav"
        aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item">
            <router-link class="nav-link" :class="{ active: $route.path === '/' }" to="/">Home</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" :class="{ active: $route.path === '/about' }" to="/about">About</router-link>
          </li>
        </ul> <!--ul-->
      </div> <!--collapse-->
    </div> <!--container-->
  </nav> <!--navbar-->
  <!-- menu end -->

  <!-- content -->
  <div class="main container mt-4">
    <router-view></router-view>
  </div> <!--main-->
  <!-- content end -->

  <!-- footer -->
  <footer class="fixed-bottom bg-dark text-light text-center py-3">
    {{ new Date().getFullYear() }}
  </footer>
  <!-- footer end -->
</template>

<style>
body {
  height: 100vh;
  background-color: #1e1e1e; 
}

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}


.navbar-brand, .nav-link {
  font-family: 'Fredoka One', sans-serif;
  font-size: 18px;
}

footer {
  width: 100%;
  height: 56px;
}
</style>

