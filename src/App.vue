<template>
  <Navbar />
  <Hero />
</template>

<script>
import Navbar from "./components/navbar/Navbar.vue";
import Hero from "./components/hero/Hero.vue";

export default {
  components: {
    Navbar,
    Hero,
  },
};
</script>


<style lang="scss" src="./styles/style.scss" ></style>