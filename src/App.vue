<template>
  <div id="app">
    <TheHeader />
    <Hero />
    <Advantages />
    <HowWeDoIt />
    <TheButton />
  </div>
</template>

<script>
import TheHeader from "@/components/layouts/TheHeader.vue";
import Hero from "@/components/hero/Hero.vue";
import Advantages from "@/components/Advantages.vue";
import HowWeDoIt from "@/components/HowWeDoIt.vue";
import TheButton from "@/components/ui/TheButton.vue";


export default {
  name: "App",
  components: {
    TheHeader,
    Hero,
    Advantages,
    HowWeDoIt,
    TheButton
  },
};
</script>

<style>
@font-face {
  font-family: "TT Travels";
  src: url("../src/assets/fonts/TTTravels-Regular.ttf") format("truetype");
}
@font-face {
  font-family: "TT Travels Medium";
  src: url("../src/assets/fonts/TTTravels-Medium.ttf") format("truetype");
}
@font-face {
  font-family: "Travels Light";
  src: url("../src/assets/fonts/TTTravels-Light.ttf") format("truetype");
}
@font-face {
  font-family: "Travels DemiBold";
  src: url("../src/assets/fonts/TTTravels-DemiBold.ttf") format("truetype");
}
@font-face {
  font-family: "Travels Bold";
  src: url("../src/assets/fonts/TTTravels-Bold.ttf") format("truetype");
}

* {
  padding: 0;
  margin: 0;
  border: 0;
}

*,
*:before,
*:after {
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
}

#app {
  font-family: TT Travels, sans-serif;
  font-size: 18px;
  line-height: inherit;
  max-width: 1440px;
  margin: 0 auto;
  text-align: center;
  color: #404040;
  position: relative;
}

ul {
  list-style: none;
}

.container {
  max-width: 1440px;
  margin: 0 auto;
  padding: 0 60px;
}

h1.hero-title {
  font-weight: 400;
  font-size: 76px;
  line-height: inherit;
}

h1 {
  font-weight: 400;
  font-size: 48px;
  line-height: 58px;
}

h2 {
  font-weight: 400;
  font-size: 44px;
  /* line-height: 53px; */
}

h3 {
  font-family: TT Travels Medium, sans-serif;
  font-weight: 500;
  font-size: 34px;
  /* line-height: 41px; */
}

h4 {
  font-family: TT Travels Medium, sans-serif;
  font-weight: 500;
  font-size: 24px;
  line-height: 31px;
}

h5 {
  font-size: 19px;
  line-height: 25px;
}

h6 {
  font-family: TT Travels Medium, sans-serif;
  font-size: 16px;
  line-height: 21px;
  font-weight: 500;
}

a {
  text-decoration: none;
}

button {
  cursor: pointer;
}
</style>
