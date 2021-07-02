<template>
  <nav>
    <div class="container">
      <div class="logo">
        <img
          :src="!isOpen ? '/images/logo-light.png' : '/images/logo.png'"
          alt="logo"
        />
      </div>

      <ul :class="`menu ${!isOpen && 'open'}`">
        <li><a href="#" class="active">Home</a></li>
        <li><a href="#">Find a doctor</a></li>
        <li><a href="#">Apps</a></li>
        <li><a href="#">Tesimonials</a></li>
        <li><a href="#">About us</a></li>
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
  },
};
</script>

<style scoped lang="scss" src="./Navbar.scss"></style>
