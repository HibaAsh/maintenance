<template>
  <div class="home">
        <nav class="navbar navbar-expand-md bg-dark navbar-dark fixed-top">
          <div class="container-fluid d-flex justify-content-between">
              <router-link to="/" class="navbar-brand text-light">Maintenance</router-link>
              <button class="navbar-toggler" data-bs-toggle="collapse" data-bs-target="#dropdownCollapse" aria-expanded="true">
                  <span class="navbar-toggler-icon"></span>
              </button>
              <div class="collapse navbar-collapse justify-content-end" id="dropdownCollapse">  
                  <ul class="navbar-nav">
                      <li class="nav-item me-3"><a href="#" class="nav-link"><span class="bi bi-printer-fill"></span> Print</a></li>
                      <li class="nav-item me-3"><router-link to="/report" class="nav-link"><span class="bi bi-flag-fill"></span> Report</router-link></li>
                      <li class="nav-item me-3"><a href="#" class="nav-link"><span class="bi bi-translate"></span> Translate</a></li>
                      <li class="nav-item me-3"><a href="#" class="nav-link"><span class="bi bi-tools"></span> Maintenance</a></li>
                  </ul>
              </div>
          </div>
        </nav>
        <router-view/>
        <footer class="bg-dark text-light py-3 fixed-bottom">
          <p class="p-0 m-0">Hiba Allah Shakoof &copy; 2023</p>
        </footer>
    </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #DC3545;
}

.nav-link:active{
  color: #DC3545;
}

body {
  /*  expand body to fill page heigth  */
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  background-image: url("./assets/wallpaper.png");
  background-size: cover;
}
</style>
