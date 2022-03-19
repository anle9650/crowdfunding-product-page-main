<template>
  <div class="container-lg">
    <nav class="navbar navbar-expand-lg navbar-dark pt-4">
      <a class="navbar-brand" href="#">crowdfund</a>
      <button
        class="navbar-toggler border-0"
        type="button"
        data-toggle="collapse"
        data-target="#navbarNav"
        aria-controls="navbarNav"
        aria-expanded="false"
        aria-label="Toggle navigation"
        @click="opened = !opened"
      >
        <img :src="require(`../assets/images/${opened ? 'icon-close-menu' : 'icon-hamburger'}.svg`)" alt="hamburger">
      </button>
      <div class="collapse navbar-collapse justify-content-end mt-4 mt-lg-0" id="navbarNav">
        <ul class="navbar-nav list-group">
          <li class="nav-item list-group-item p-lg-0 mr-lg-3">
            <a class="nav-link" href="#">About</a>
          </li>
          <li class="nav-item list-group-item p-lg-0 mr-lg-3">
            <a class="nav-link" href="#">Discover</a>
          </li>
          <li class="nav-item list-group-item p-lg-0">
            <a class="nav-link" href="#">Get Started</a>
          </li>
        </ul>
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  name: "Navbar",
  data() {
    return {
      opened: false
    }
  }
};
</script>

<style scoped>
.navbar-brand {
  color: white;
  font-weight: 700;
  font-size: 2rem;
}
.navbar-nav {
  border-radius: 10px;
}
.navbar-nav .nav-link {
  color: black;
  font-weight: 500;
}
button.navbar-toggler img {
  width: 1.5rem;
}

@media screen and (max-width: 992px) {
  .navbar-nav .nav-link:hover {
    color: black;
  }
}

@media screen and (min-width: 992px) {
  .navbar-brand {
    font-size: 1.5rem;
  }
  li.nav-item.list-group-item {
    border: none;
    background-color: transparent;
  }
  .navbar-nav .nav-link {
    color: white;
    font-weight: 400;
  }
}
</style>
