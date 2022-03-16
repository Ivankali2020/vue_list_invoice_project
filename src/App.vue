<template>

  <div class="container">
    <nav class="navbar navbar-expand-lg navbar-light  bg-light">
      <div class="container-fluid">
        <a class="navbar-brand" href="#">Navbar</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav ms-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <router-link to="/" class="nav-link " aria-current="page">Home</router-link>
            </li>
            <li class="nav-item">
              <router-link to="/about" class="nav-link" >About</router-link>
            </li>
            <li class="nav-item">
              <router-link to="/contact" class="nav-link" >Contact</router-link>
            </li>
          </ul>

        </div>
      </div>
    </nav>
    <div class="row">
        <router-view/>
    </div>
  </div>
</template>

<style lang="scss">
  @import "~bootstrap/scss/bootstrap.scss";
  .nav-link.active{
    color: #42b983 !important;
  }
  .router-link-exact-active{
    color: #42b983 !important;
  }
</style>
