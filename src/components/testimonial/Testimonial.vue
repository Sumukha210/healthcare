<template>
  <main class="margin-top" id="testimonial">
    <div v-if="loading === true" style="text-align: center">
      <h3>loading....</h3>
    </div>

    <div class="primary-container" v-if="testimonials.length">
      <header>
        <h2 class="heading-2">What our customer are saying</h2>
      </header>

      <div class="content">
        <div ref="left" class="left">
          <img :src="testimonials[currentItem].avatar" alt="" />
          <div class="left--content">
            <h3 ref="name">{{ testimonials[currentItem].first_name }}</h3>
            <p ref="email">{{ testimonials[currentItem].email }}</p>
          </div>
        </div>

        <div ref="right" class="right">
          <p>
            "Hello, my name is {{ testimonials[currentItem].first_name }}
            {{ testimonials[currentItem].last_name }} Lorem ipsum dolor sit amet
            consectetur adipisicing elit. Recusandae expedita reprehenderit
            perspiciatis ad dolor soluta cumque ratione sapiente quam quia
            itaque quo amet consequatur maiores repellat, doloribus quos.You can
            contact me at any time "
          </p>
        </div>
      </div>

      <img src="/images/light-dots.png" alt="" class="dots-img" />
    </div>

    <div class="bottom">
      <div
        :class="['arrow', 'left', `${currentItem <= 0 && 'inactive'}`]"
        @click="prev()"
      >
        <i class="fas fa-arrow-left"></i>
      </div>
      <div class="dots-container">
        <div
          :class="[
            'dots',
            `${currentItem + 1 === item.id ? 'active' : 'inactive'}`,
          ]"
          v-for="item in testimonials"
          :key="item.id"
          @click="dots(item)"
        ></div>
      </div>
      <div class="arrow right" @click="next()">
        <i class="fas fa-arrow-right"></i>
      </div>
    </div>
  </main>
</template>

<script >
import axios from "axios";
import { gsap } from "gsap";

export default {
  data() {
    return {
      testimonials: [],
      loading: false,
      error: {},
      currentItem: 0,
    };
  },
  methods: {
    next() {
      this.animate();
      if (this.currentItem >= this.testimonials.length - 1) {
        this.currentItem = 0;
      } else {
        this.currentItem = this.currentItem + 1;
      }
    },
    prev() {
      this.animate();
      if (this.currentItem > 0) {
        this.currentItem = this.currentItem - 1;
      }
    },

    dots(item) {
      this.animate();
      this.currentItem = item.id - 1;
    },

    animate() {
      const { left, name, email, right } = this.$refs;
      const timeline = gsap.timeline({ defaults: { duration: 1 } });
      timeline
        .from(left, { opacity: 0, x: -50, ease: "power3" })
        .from([name, email], { opacity: 0, stagger: 0.5 }, "-=0.5")
        .from(right, { opacity: 0, x: 50, ease: "power3" }, "-=0.5");
    },
  },

  mounted() {
    this.loading = true;
    this.$nextTick(async () => {
      this.loading = false;
      try {
        const res = await axios.get("https://reqres.in/api/users?page=1");
        this.testimonials = res.data.data.slice(0, 4);
      } catch (error) {
        this.error = JSON.stringify(error);
      }
    });
  },
};
</script>


<style lang="scss" scoped  src="./Testimonial.scss" ></style>