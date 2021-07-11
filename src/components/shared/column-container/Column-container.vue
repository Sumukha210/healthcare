<template>
  <div id="apps" ref="apps" class="primary-container margin-top">
    <div class="left" :style="{ order: imgFirst ? 1 : 2 }">
      <img ref="img" :src="imgUrl" alt="hero image" />
    </div>

    <div class="right" :style="{ order: imgFirst ? 2 : 1 }">
      <div class="info">
        <h2 ref="heading" class="heading-2">
          {{ title }}
        </h2>
        <p class="content" ref="content">
          {{ content }}
        </p>
        <button class="btn btn-outline-primary" ref="btn">{{ btnName }}</button>
      </div>
    </div>
  </div>
</template>


<style scoped lang="scss" src="./Column-container.scss"></style>

<script>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

export default {
  props: {
    imgFirst: Boolean,
    title: String,
    content: String,
    imgUrl: String,
    btnName: String,
  },
  mounted() {
    const { heading, content, btn, img, apps } = this.$refs;
    const timeline = gsap.timeline({
      defaults: {
        duration: 0.6,
      },
      scrollTrigger: {
        trigger: apps,
        start: "top center",
        end: "bottom top",
      },
    });
    gsap.registerPlugin(ScrollTrigger);

    timeline
      .from([img], {
        x: this.imgFirst ? -80 : 80,
        opacity: 0,
      })
      .from([heading, content], {
        x: this.imgFirst ? 80 : -80,
        opacity: 0,
        stagger: 0.6,
      })
      .to(btn, { visibility: "visible", opacity: 1 }, "-=0.3");
  },
};
</script>