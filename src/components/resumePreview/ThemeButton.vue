<template>
  <i
    class="bx change-theme"
    :class="{ 'bx-moon': currentTheme === 'light', ' bx-sun': currentTheme !== 'light' }"
    title="Theme"
    id="theme-button"
    ref="themeButton"
    @click="changeTheme"
  ></i>
</template>

<script>
export default {
  name: 'ThemeButton',
  data() {
    return {
      currentTheme: 'light'
    }
  },
  watch: {
    currentTheme() {
      this.persistCurrentTheme()
      this.updateClasses()
    }
  },
  mounted() {
    this.currentTheme = localStorage.getItem('selected-theme')
  },
  methods: {
    changeTheme() {
      this.currentTheme = this.currentTheme === 'light' ? 'dark' : 'light'

      const themeButton = this.$refs.themeButton
      themeButton.classList.toggle('bx-moon')
    },
    persistCurrentTheme() {
      localStorage.setItem('selected-theme', this.currentTheme)
    },
    updateClasses() {
      if (this.currentTheme === 'light') {
        document.body.classList.remove('dark-theme')
      } else {
        document.body.classList.contains('dark-theme') || document.body.classList.add('dark-theme')
      }
    }
  }
}
</script>

<style></style>
