<template>
  <nav>
    <div class="secondary-container">
      <div class="logo">
        <img
          :src="!isOpen ? '/images/logo-light.png' : '/images/logo.png'"
          alt="logo"
        />
      </div>

      <ul :class="`menu ${!isOpen && 'open'}`">
        <li @click="closeMenu()"><a href="#home" class="active">Home</a></li>
        <li @click="closeMenu()"><a href="#services">Services</a></li>
        <li @click="closeMenu()"><a href="#apps">Apps</a></li>
        <li @click="closeMenu()"><a href="#tesimonials">Tesimonials</a></li>
        <li @click="closeMenu()"><a href="#articles">Articles</a></li>
      </ul>

      <div class="mobileMenu" @click="handleMenu()">
        <i
          :class="isOpen ? 'fas fa-bars' : 'fas fa-times'"
          :style="{ color: !isOpen ? 'white' : 'black' }"
        ></i>
      </div>
    </div>

    <div class="overlay" v-if="!isOpen"></div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      isOpen: true,
    };
  },

  methods: {
    handleMenu() {
      this.isOpen = !this.isOpen;
      if (!this.isOpen) {
        document.body.style.overflow = "hidden";
      } else {
        document.body.style.overflow = "initial";
      }
    },

    closeMenu() {
      this.isOpen = true;
      document.body.style.overflow = "initial";
    },
  },
};
</script>

<style scoped lang="scss" src="./Navbar.scss"></style>
