<template>
  <header class="l-header" id="header">
    <nav class="nav bd-container">
      <a href="#" class="nav__logo">Doe</a>
      <div class="nav__menu" id="nav-menu" ref="navMenuRef">
        <ul class="nav__list">
          <li class="nav__item">
            <a href="#home" class="nav__link active-link">
              <i class="bx bx-home nav__icon"></i>Home
            </a>
          </li>

          <li class="nav__item">
            <a href="#profile" class="nav__link"> <i class="bx bx-user nav__icon"></i>Profile </a>
          </li>

          <li class="nav__item">
            <a href="#education" class="nav__link">
              <i class="bx bx-book nav__icon"></i>Education
            </a>
          </li>

          <li class="nav__item">
            <a href="#skills" class="nav__link"> <i class="bx bx-receipt nav__icon"></i>Skills </a>
          </li>

          <li class="nav__item">
            <a href="#experience" class="nav__link">
              <i class="bx bx-briefcase-alt nav__icon"></i>Experience
            </a>
          </li>

          <li class="nav__item">
            <a href="#certificates" class="nav__link">
              <i class="bx bx-award nav__icon"></i>Certificates
            </a>
          </li>

          <li class="nav__item">
            <a href="#references" class="nav__link">
              <i class="bx bx-link-external nav__icon"></i>References
            </a>
          </li>
        </ul>
      </div>
      <div class="nav__toggle" id="nav-toggle" ref="navToggleRef">
        <i class="bx bx-grid-alt"></i>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'HeaderComponent',

  mounted() {
    this.showMenu(this.$refs.navToggleRef.id, this.$refs.navMenuRef.id)
  },
  methods: {
    showMenu(toggleId, navId) {
      console.log(toggleId)
      const toggle = document.getElementById(toggleId)
      const nav = document.getElementById(navId)
      console.log(nav, 'this is the togglle')
      // validate that variables exist
      if (toggle && nav) {
        toggle.addEventListener('click', () => {
          // we  add the show-menu class to the div tag with the nav__menu class
          nav.classList.toggle('show-menu')
        })
      }
    }
  }
}
</script>

<style></style>
