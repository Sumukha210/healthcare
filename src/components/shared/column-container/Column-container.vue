<template>
  <div class="container margin-top">
    <div class="left" :style="{ order: imgFirst ? 1 : 2 }">
      <img :src="imgUrl" alt="hero image" />
    </div>

    <div class="right" :style="{ order: imgFirst ? 2 : 1 }">
      <div class="info">
        <h2 class="heading-2">
          {{ title }}
        </h2>
        <p class="content">
          {{ content }}
        </p>
        <button class="btn btn-outline-primary">{{ btnName }}</button>
      </div>
    </div>
  </div>
</template>


<style scoped lang="scss" src="./Column-container.scss"></style>

<script>
export default {
  props: {
    imgFirst: Boolean,
    title: String,
    content: String,
    imgUrl: String,
    btnName: String,
  },
};
</script>