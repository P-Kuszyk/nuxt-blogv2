<script setup>
const mobileMenu = ref(false)
const showMenu = () => {
  mobileMenu.value = !mobileMenu.value
  console.log(mobileMenu.value)
}
</script>

<template>
 <nav class="navbar" role="navigation" aria-label="main navigation">
  <div class="navbar-brand">
    <a class="navbar-item" href="https://bulma.io">
      <img src="https://bulma.io/assets/brand/Bulma%20Logo%20Black.png" width="112" height="28">
    </a>

    <a role="button" 
    class="navbar-burger" 
    aria-label="menu" 
    aria-expanded="false" 
    data-target="navbarBasicExample"
    @click="showMenu"
    >
      <span aria-hidden="true"></span>
      <span aria-hidden="true"></span>
      <span aria-hidden="true"></span>
    </a>
  </div>

  <div id="navbarBasicExample" :class="{'navbar-menu': !mobileMenu}">
    <div class="navbar-start">
      <NuxtLink to="/" class="navbar-item">
        Home
      </NuxtLink>

      <NuxtLink to="/api" class="navbar-item">
        API
      </NuxtLink>

      <NuxtLink to="/about" class="navbar-item">
        About
      </NuxtLink>

      <a href="/pictures" class="navbar-item">
        Pictures
      </a>

      <div class="navbar-item has-dropdown is-hoverable">

        <div class="navbar-dropdown">
          <a class="navbar-item">
            About
          </a>
          <a class="navbar-item">
            Jobs
          </a>
          <a class="navbar-item">
            Contact
          </a>
          <hr class="navbar-divider">
          <a class="navbar-item">
            Report an issue
          </a>
        </div>
      </div>
    </div>

    <div class="navbar-end">
      <div class="navbar-item">
        <div class="buttons">
          <a class="button is-primary">
            <strong>Sign up</strong>
          </a>
          <a class="button is-light">
            Log in
          </a>
        </div>
      </div>
    </div>
  </div>
</nav>
</template>
<style scoped lang="scss">
.navbar {
  background-color: #058549;
}

.navbar-menu {
  position: absolute;
  left: 10%;
  width: 100%;
}

.navbar-menu a {
  color: #000;

}

.logo {
  @media screen and (max-width: 1023px) {
    display: none;
  }
}
</style>