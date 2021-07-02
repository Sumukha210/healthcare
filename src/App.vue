<template>
  <Navbar />
  <Hero />
  <Services />
  <ColumnContainer
    :btnName="'Learn more'"
    :title="'Leading healthcare providers'"
    :imgFirst="true"
    :imgUrl="'/images/leading-healthcare-providers.png'"
    :content="`Trafalgar provides progressive, and affordable healthcare, accessible on mobile and online for everyone. To us, it’s not just work. We take pride in the solutions we deliver`"
  />

  <ColumnContainer
    :btnName="'Download'"
    :title="'Download our mobile apps'"
    :imgFirst="false"
    :imgUrl="'/images/download-apps.png'"
    :content="`Our dedicated patient engagement app and web portal allow you to access information instantaneously (no tedeous form, long calls, or administrative hassle) and securely`"
  />
</template>

<script>
import Navbar from "./components/navbar/Navbar.vue";
import Hero from "./components/hero/Hero.vue";
import Services from "./components/services/Services.vue";
import ColumnContainer from "./components/shared/column-container/Column-container.vue";

export default {
  components: {
    Navbar,
    Hero,
    Services,
    ColumnContainer,
  },
};
</script>


<style lang="scss" src="./styles/style.scss" ></style>