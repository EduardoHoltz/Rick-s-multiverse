<template>
  <div class="container mt-4 text-body-secondary">
    <div class="card">
      <h1 class="text-center mb-4">About</h1>
      <div class="card-body">
        <div class="text-center mb-4">
          <img src="../assets/morty.svg" alt="Morty" class="img-fluid" style="max-width: 200px;">
        </div>
        <h3>Project Description</h3>
        <p>The "Rick and Morty Character Viewer" project is a web application that allows fans of the popular animated
          series "Rick and Morty" to explore information about the show's characters. Its main objective is to provide an
          easy-to-use platform for discovering intriguing details about each character, including their names, status,
          species, and illustrative images.</p>
        <hr>
        <h3>Technologies and Tools</h3>
        <p>The "Rick and Morty Character Viewer" project utilizes Vue.js, Bootstrap, and Animate.css to create a
          responsive and visually appealing web application. By consuming the public API of "Rick and Morty" through the
          Fetch API, the application displays information about the characters of the series, providing an engaging and
          user-friendly experience.</p>
        <hr>
      </div> <!--card body-->
    </div> <!--card-->
  </div> <!--container-->
</template>

<style scoped>
.container {
  max-width: 800px;
}

.card {
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  padding: 20px;
}

h1 {
  font-size: 36px;
  font-weight: bold;
  color: #43A047;
}

h3 {
  font-size: 24px;
  font-weight: bold;
  color: #43A047;
  margin-bottom: 10px;
}

p {
  font-size: 16px;
  line-height: 1.6;
  margin-bottom: 20px;
}

hr {
  border: 0;
  border-top: 2px solid #43A047;
  margin: 20px 0;
}

@media (max-width: 576px) {
  h1 {
    font-size: 24px;
  }

  h3 {
    font-size: 20px;
  }

  p {
    font-size: 14px;
  }
}
</style>
