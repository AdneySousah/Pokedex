<script>
import {ref} from 'vue'
</script>

<template>

  <nav class="navbar navbar-expand-lg navbar-dark bg-primary">
  <div class="container-fluid">
    <router-link  class="navbar-brand" to="/">
      <img src="https://cdn-icons-png.flaticon.com/512/188/188987.png" alt="Bootstrap" width="30" height="24">
    </router-link >
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="navbar-nav">
        <li class="nav-item">
          <router-link  class="nav-link" aria-current="page" to="/">Home</router-link >
        </li>
        <li class="nav-item">
          <router-link  class="nav-link" to="/about">About</router-link >
        </li>
       
      </ul>
    </div>
  </div>
</nav>

<!-- content -->
 <div class="main">
    <router-view></router-view>

 </div>

 <footer class="bg-primary text-light">
  Desining in{{ new Date().getFullYear() }}
 </footer>
</template>

<style>
body{

height: 100vh;
background: linear-gradient(90deg, rgba(69,228,252,1) 0%, rgba(29,58,253,0.976908263305322) 43%, rgba(69,228,252,1) 100%);


}

footer{
  position:fixed;
  bottom: 0;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 56px;
}
</style>