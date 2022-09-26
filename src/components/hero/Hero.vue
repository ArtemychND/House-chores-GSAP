<template>
  <section class="hero">
    <div class="hero__wrapper">
      <div class="hero__banner">
        <img src="@/assets/img/main-banner.svg" alt="banner" />
      </div>
      <div class="hero__title">
        <div class="text-wrap">
          <h1 class="hero-title">Уборка квартир в Киеве</h1>
          <p class="hero-descr">
            Мы уберем у вас дома или в офисе. Наведем чистоту после ремонта и
            проведем генеральную уборку.
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

export default {
  mounted() {
    const t1 = gsap.timeline({ defaults: { duration: 1 } });
    t1.from(".hero-title", { opacity: 0, x: 30 }).from(".hero-descr", {
      opacity: 0,
      y: 30,
    });

  },
};
</script>

<style scoped>
.hero__wrapper {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.hero__banner,
.hero__title {
  flex: 1 1 50%;
}

.hero__title {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: start;
}

.text-wrap {
  max-width: 400px;
}
.text-wrap p {
  margin-top: 30px;
  line-height: 25px;
}

@media (max-width: 1150px) {
  .hero__wrapper {
    position: relative;
  }
  .hero__title {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: #000;
  }
}
</style>