<template>
  <section class="header">
    <div class="header__logo">
      <img src="@/assets/img/Logo.svg" alt="logo" />
    </div>
    <div class="header__switcher">
      <button
        @click="switchMode = 'house'"
        :class="{ active: switchMode === 'house' }"
      >
        Дом
      </button>
      <button
        @click="switchMode = 'office'"
        :class="{ active: switchMode === 'office' }"
      >
        Офис
      </button>
    </div>
    <nav>
      <ul class="header__nav" :class="{ show: isMenuActive }">
        <li>После ремонта</li>
        <li>Генеральная уборка</li>
        <li>Регулярная уборка</li>
        <li>Мойка окон</li>
      </ul>
    </nav>
    <div class="header__info">
      <h6>+380 67 401 69 77</h6>
      <span>|</span>
      <h6>24/7</h6>
    </div>
    <div class="menu-toggle" :class="{ on: isMenuActive }" @click="toggleMenu">
      <div class="menu-toggle_one"></div>
      <div class="menu-toggle_two"></div>
    </div>
  </section>
</template>

<script>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

export default {
  data() {
    return {
      switchMode: "house",
      isMenuActive: false,
      headerActive: false
    };
  },
  methods: {
    toggleMenu() {
      this.isMenuActive = !this.isMenuActive;
    },
  },
  mounted() {
    ScrollTrigger.create({
      trigger: "#app",
      start: "7% 7%",
      toggleClass: {targets: ".header", className: "move"},
    })
  }
};
</script>

<style scoped>
.header {
  display: flex;
  justify-content: space-around;
  align-items: center;
  position: fixed;
  top: 20px;
  left: 0;
  right: 0;
  z-index: 200;
}

.move {
  background-color: #fff;
  padding: 20px 0;
  top: 0;
}

.header__switcher {
  display: flex;
  justify-content: space-around;
  align-items: center;
  width: 131px;
  height: 37px;
  padding: 3px;
  top: calc(50% - 37px / 2 - 0.5px);
  background: #ffffff;
  border: 1px solid #e2e8f0;
  border-radius: 48px;
}
.header__switcher button {
  outline: none;
  padding: 8px 12px;
  border-radius: 34px;
  background: #ffffff;
}
.header__switcher button.active {
  background: #5a30f0;
  color: #fff;
}

.header__nav {
  display: flex;
  align-items: center;
  font-weight: 500;
  font-size: 16px;
  line-height: 19px;
  letter-spacing: 0.2px;
}
.header__nav li:not(:first-child) {
  margin-left: 30px;
}

.header__info {
  display: flex;
  align-items: center;
  letter-spacing: 0.2px;
}
.header__info span {
  margin: 0 15px;
}

/* Mobile menu */

.menu-toggle {
  width: 20px;
  cursor: pointer;
  display: none;
}

.menu-toggle.on .menu-toggle_one {
  transform: rotate(45deg) translate(3px, 4px);
}

.menu-toggle.on .menu-toggle_two {
  transform: rotate(-45deg) translate(3px, -4px);
}

.menu-toggle .menu-toggle_one,
.menu-toggle .menu-toggle_three,
.menu-toggle .menu-toggle_two {
  width: 100%;
  height: 2px;
  background: #000;
  margin: 8px auto;
  backface-visibility: hidden;
  -moz-transition-duration: 0.3s;
  -o-transition-duration: 0.3s;
  -webkit-transition-duration: 0.3s;
  transition-duration: 0.3s;
  border-radius: 20px;
}

@media (max-width: 1150px) {
  .header__nav {
    display: none;
  }
  .header__nav.show {
    display: flex;
    flex-direction: column;
    position: fixed;
    top: 80px;
    right: 60px;
    background-color: #fff;
    border-radius: 8px;
  }
  .header__nav li {
    padding: 5px;
  }
  .header__nav li:not(:first-child) {
    margin-left: 0;
  }
  .menu-toggle {
    display: block;
  }
}
</style>