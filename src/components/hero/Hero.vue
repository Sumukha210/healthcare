<template>
  <div class="primary-container" id="hero">
    <div class="left">
      <div class="content">
        <h1 ref="heading" class="heading">
          Virtual healthcare <br />
          for you
        </h1>

        <p ref="subTitle">
          Trafalgar provides progressive, and affordable healthcare,
          <br />accessible on mobile and online for <br />
          everyone
        </p>
        <button ref="btn" class="btn btn-primary">Consult today</button>
      </div>
    </div>

    <div class="right">
      <img src="/images/hero.png" ref="mainImg" alt="hero image" />
    </div>

    <div class="dots">
      <img src="/images/dots.png" ref="dots" alt="" />
    </div>
  </div>
</template>


<style scoped lang="scss" src="./Hero.scss">
</style>

<script>
import { gsap } from "gsap";
export default {
  mounted() {
    const timeline = gsap.timeline({ duration: 1 });
    const { dots, mainImg, heading, subTitle, btn } = this.$refs;

    timeline
      .from([heading, subTitle, btn], {
        y: -30,
        opacity: 0,
        stagger: 0.3,
      })
      .to(btn, {
        opacity: 1,
        // x: 0,
        ease: "bounce.out",
      })
      .from(
        mainImg,
        {
          y: 50,
          opacity: 0,
        },
        "-=0.6"
      )
      .from(dots, { left: -10, opacity: 0 }, "-=1.4");
  },
};
</script>