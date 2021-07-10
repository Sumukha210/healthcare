<template>
  <main class="margin-top" id="tesimonials">
    <div v-if="loading === true" style="text-align: center">
      <h3>loading....</h3>
    </div>

    <div class="primary-container" v-if="testimonials.length">
      <header>
        <h2 class="heading-2">What our customer are saying</h2>
      </header>

      <div class="content">
        <div class="left">
          <img :src="testimonials[currentItem].avatar" alt="" />
          <div class="left--content">
            <h3>{{ testimonials[currentItem].first_name }}</h3>
            <p>{{ testimonials[currentItem].email }}</p>
          </div>
        </div>

        <div class="right">
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
          @click="currentItem = item.id - 1"
        ></div>
      </div>
      <div class="arrow right" @click="next()">
        <i class="fas fa-arrow-right"></i>
      </div>
    </div>
  </main>
</template>

<script>
import axios from "axios";

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
      if (this.currentItem >= this.testimonials.length - 1) {
        this.currentItem = 0;
      } else {
        this.currentItem = this.currentItem + 1;
      }
    },
    prev() {
      if (this.currentItem > 0) {
        this.currentItem = this.currentItem - 1;
      }
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