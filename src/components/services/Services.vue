<template>
  <main class="margin-top" id="services">
    <div class="container">
      <header>
        <h2 class="heading-2">Our Services</h2>
        <p>
          We provide to you the best choiches for you. Adjust it to your health
          needs and make sure your undergo treatment with our highly qualified
          doctors you can consult with us which type of service is suitable for
          your health
        </p>
      </header>

      <div class="services">
        <div class="card-container">
          <div
            class="card"
            v-for="{ img, title, content } in services"
            :key="title"
          >
            <div class="card-header">
              <img :src="img" alt="" />
              <div class="card-body">
                <div class="card-title">
                  {{ title }}
                </div>
                <div class="card-subTitle">
                  {{ content }}
                </div>
              </div>
            </div>
          </div>
          <img src="/images/dots.png" alt="" class="dotBgImg" />
        </div>
      </div>

      <div class="btn-container">
        <button class="btn btn-outline-primary">Learn more</button>
      </div>
    </div>

    <img src="/images/bg-services.png" alt="" class="LargeBgImg" />
  </main>
</template>


<style scoped lang="scss" src="./Services.scss"></style>

<script>
export default {
  data() {
    return {
      services: [
        {
          img: "/images/servicesIcon1.png",
          title: "Search doctor",
          content:
            "Choose your doctor from thousands of specialist, general, and trusted hospitals",
        },
        {
          img: "/images/servicesIcon2.png",
          title: "Online pharmacy",
          content:
            "Buy  your medicines with our mobile application with a simple delivery system",
        },
        {
          img: "/images/servicesIcon3.png",
          title: "Consultation",
          content:
            "Free consultation with our trusted doctors and get the best recomendations",
        },
        {
          img: "/images/servicesIcon4.png",
          title: "Details info",
          content:
            "Free consultation with our trusted doctors and get the best recomendations",
        },
        {
          img: "/images/servicesIcon5.png",
          title: "Emergency carer",
          content:
            "You can get 24/7 urgent care for yourself or your children and your lovely family",
        },
        {
          img: "/images/servicesIcon6.png",
          title: "Tracking",
          content: "Track and save your medical history and health data  ",
        },
      ],
    };
  },
};
</script>