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
        <li @click="closeMenu('hero')">
          <span
            :class="currentEle === 'hero' && 'active'"
            @click="currentEle = 'hero'"
            >Home</span
          >
        </li>

        <li @click="closeMenu('services')">
          <span
            :class="currentEle === 'services' && 'active'"
            @click="currentEle = 'services'"
            >Services</span
          >
        </li>

        <li @click="closeMenu('apps')">
          <span
            :class="currentEle === 'apps' && 'active'"
            @click="currentEle = 'apps'"
            >Apps</span
          >
        </li>

        <li @click="closeMenu('testimonial')">
          <span
            :class="currentEle === 'testimonial' && 'active'"
            @click="currentEle = 'testimonial'"
            >Tesimonials</span
          >
        </li>

        <li @click="closeMenu('articles')">
          <span
            :class="currentEle === 'articles' && 'active'"
            @click="currentEle = 'articles'"
            >Articles</span
          >
        </li>
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
import { gsap } from "gsap";
import { ScrollToPlugin } from "gsap/ScrollToPlugin";
import { ScrollTrigger } from "gsap/ScrollTrigger";

export default {
  data() {
    return {
      isOpen: true,
      currentEle: "hero",
    };
  },

  mounted() {
    gsap.registerPlugin(ScrollToPlugin, ScrollTrigger);
    this.updateCurrentEle("#hero");
    this.updateCurrentEle("#services");
    this.updateCurrentEle("#apps");
    this.updateCurrentEle("#testimonial");
    this.updateCurrentEle("#articles");
  },

  methods: {
    handleMenu() {
      this.isOpen = !this.isOpen;
      if (!this.isOpen) {
        document.body.style.overflow = "hidden";
        gsap.from("li", {
          opacity: 0,
          x: -20,
          duration: 1.6,
          stagger: 0.3,
          ease: "power3",
        });
      } else {
        document.body.style.overflow = "initial";
      }
    },

    updateCurrentEle(val) {
      ScrollTrigger.create({
        trigger: val,
        // offsetY: 300,
        start: "-100",
        // start: "top",
        onEnter: (self) => {
          this.currentEle = self.trigger.id;
        },

        onEnterBack: (self) => {
          this.currentEle = self.trigger.id;
        },
      });
    },

    closeMenu(val) {
      gsap.to(window, {
        duration: 1.7,
        scrollTo: { y: `#${val}`, offsetY: 100 },
      });

      this.isOpen = true;
      document.body.style.overflow = "initial";
    },
  },
};
</script>

<style scoped lang="scss" src="./Navbar.scss"></style>
