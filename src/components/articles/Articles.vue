<template>
  <section class="margin-top" id="articles">
    <div class="primary-container">
      <h2 class="heading-2">Check out our latest article</h2>

      <div class="content">
        <div class="card" v-for="item in articles" :key="item.title">
          <img :src="item.img" alt="" class="card-img-top" />
          <div class="card-body">
            <h3 class="card-title">
              {{ item.title }}
            </h3>
            <p class="card-subTitle">
              {{ item.subTitle }}
            </p>
          </div>
          <div class="card-footer">
            Read more
            <span>
              <i class="fas fa-arrow-right"></i>
            </span>
          </div>
        </div>
      </div>

      <div class="btn-container">
        <button class="btn btn-outline-primary">View all</button>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      articles: [
        {
          title: `Disease detection, check up in the laboratory`,
          subTitle: `In this case, the role of the health laboratory is very important to do a disease detection...`,
          img: "/images/article-1.png",
        },
        {
          title: `Herbal medicines that are safe for consumption`,
          subTitle: `Herbal medicine is very widely used at this time because of its very good for your health...`,
          img: "/images/article-2.png",
        },
        {
          title: `Disease detection, check up in the laboratory`,
          subTitle: `Herbal medicine is very widely used at this time because of its very good for your health...`,
          img: "/images/article-3.png",
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped src="./Articles.scss" ></style>