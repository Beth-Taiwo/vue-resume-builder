<template>
  <header class="l-header" id="header">
    <nav class="nav bd-container">
      <a href="#" class="nav__logo">Doe</a>
      <div class="nav__menu" :class="{ 'show-menu': shouldShowMenu }" id="nav-menu">
        <ul class="nav__list">
          <li class="nav__item">
            <a href="#home" class="nav__link active-link" @click="shouldShowMenu = false">
              <i class="bx bx-home nav__icon"></i>Home
            </a>
          </li>

          <li class="nav__item">
            <a href="#profile" class="nav__link" @click="shouldShowMenu = false">
              <i class="bx bx-user nav__icon"></i>Profile
            </a>
          </li>

          <li class="nav__item">
            <a href="#education" class="nav__link" @click="shouldShowMenu = false">
              <i class="bx bx-book nav__icon"></i>Education
            </a>
          </li>

          <li class="nav__item">
            <a href="#skills" class="nav__link" @click="shouldShowMenu = false">
              <i class="bx bx-receipt nav__icon"></i>Skills
            </a>
          </li>

          <li class="nav__item">
            <a href="#experience" class="nav__link" @click="shouldShowMenu = false">
              <i class="bx bx-briefcase-alt nav__icon"></i>Experience
            </a>
          </li>

          <li class="nav__item">
            <a href="#certificates" class="nav__link" @click="shouldShowMenu = false">
              <i class="bx bx-award nav__icon"></i>Certificates
            </a>
          </li>

          <li class="nav__item">
            <a href="#references" class="nav__link" @click="shouldShowMenu = false">
              <i class="bx bx-link-external nav__icon"></i>References
            </a>
          </li>
        </ul>
      </div>
      <div class="nav__toggle" id="nav-toggle" @click="shouldShowMenu = !shouldShowMenu">
        <i class="bx bx-grid-alt"></i>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'HeaderComponent',
  data() {
    return {
      shouldShowMenu: false
    }
  },
  mounted() {},
  methods: {
    //     linkActions() {
    //      const navLink = document.querySelectorAll(".nav__link");
    //   const navMenu = document.getElementById("nav-menu");
    //   // when we click on each nav_link, we remove the show-menu class
    //   navMenu.classList.remove("show-menu");
    //   navLink.forEach((n) => n.addEventListener("click", linkActions));
    // }
  }
}
</script>

<style></style>
