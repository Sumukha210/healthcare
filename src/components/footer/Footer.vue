<template>
  <section class="margin-top">
    <div class="secondary-container" id="footer">
      <div class="content">
        <img src="/images/logo-footer.png" alt="" />
        <p>
          Trafalgar provides progressive, and affordable <br />
          healthcare, accessible on mobile and online <br />
          for everyone
        </p>
        <p>©Trafalgar PTY LTD 2020. All rights reserved</p>
      </div>

      <div class="content">
        <h4>Company</h4>
        <ul>
          <li @click="moveUpFun('about')">About</li>
          <li @click="moveUpFun('testimonial')">Testimonial</li>
          <li @click="moveUpFun('services')">Find a doctor</li>
          <li @click="moveUpFun('apps')">Apps</li>
        </ul>
      </div>

      <div class="content">
        <h4>Region</h4>
        <ul>
          <li>Indonesia</li>
          <li>Singapore</li>
          <li>HongKong</li>
          <li>Canada</li>
        </ul>
      </div>

      <div class="content">
        <h4>Help</h4>
        <ul>
          <li>Help center</li>
          <li>Contact support</li>
          <li>Instructions</li>
          <li>How it works</li>
        </ul>
      </div>
    </div>

    <button class="up-btn" @click="moveUpFun()">
      <i class="fas fa-arrow-up"></i>
    </button>
  </section>
</template>

<style scoped lang="scss" src="./Footer.scss"></style>

<script>
import { gsap } from "gsap";
import { scrollTo } from "gsap/ScrollToPlugin";

export default {
  mounted() {
    // gsap.from(".up-btn", {
    //   bottom: "6%",
    //   yoyo: true,
    //   repeat: -1,
    //   duration: 0.8,
    //   ease: "none",
    // });

    gsap.registerPlugin(scrollTo);
  },
  methods: {
    moveUpFun(location = "hero") {
      gsap.to(window, {
        duration: 1.7,
        scrollTo: {
          y: `#${location}`,
          offsetY: location === "hero" ? 5 : 100,
        },
      });
    },
  },
};
</script>
