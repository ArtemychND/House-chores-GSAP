<template>
  <section class="how">
    <div class="how__supdescription">
      <div class="suptitle">
        <h2>Как мы убираем</h2>
      </div>
      <div class="supdesription">
        <p>
          Клинер приезжает в назначенное время со всем необходимым и сразу
          приступает к делу. Вам остаётся только оценить результат.
        </p>
      </div>
    </div>
    <div class="how__illustration">
      <div class="sidemenu">
        <h6>Как мы убираем</h6>
        <ul class="sidemenu-nav">
          <li><a class="activated" @click="setPlace">Кухня</a></li>
          <li><a @click="setPlace">Комнаты</a></li>
          <li><a @click="setPlace($event, 'bathroom')">Ванная</a></li>
          <li><a @click="setPlace">Прихожая</a></li>
        </ul>
      </div>
      <div class="illustration-image">
        <div class="image-1 img-cont">
          <button v-for="i in 7" :key="i" class="point" :class="'point' + i">
            {{ btnText }}
          </button>
        </div>
        <div class="image-2 img-cont">
          <button v-for="i in 7" :key="i" class="point" :class="'point' + i">
            {{ btnText }}
          </button>
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
  data() {
    return {
      btnText: "+",
    };
  },
  methods: {
    setPlace(e, place) {
      this.resetActiveSelector(e);

      if (place === "bathroom") {
        gsap.fromTo(
          ".image-2",
          {
            // background: `url(${require("../assets/img/illustration-bath-bg.png")}) 0 0 no-repeat`,
            x: "360px",
            y: "-120%",
            zIndex: 200
          },
          {
            x: 0,
            y: "-100%",
            zIndex: 10,
            duration: 2,
          }
        );
      } else {
        gsap.fromTo(
          ".image-1",
          {
            // background: `url(${require("../assets/img/illustration-bg.png")}) 0 0 no-repeat`,
            x: "360px",
            y: "-200px",
            zIndex: 200
          },
          {
            x: 0,
            y: 0,
            zIndex: 10,
            duration: 2,
          }
        );
      }

      setTimeout(() => document.querySelectorAll(".point").forEach((el) => el.style.display = "block"), 2000)
    },
    resetActiveSelector(e) {
      document.querySelectorAll(".point").forEach((el) => el.style.display = "none")
      document.querySelectorAll(".img-cont").forEach(el => el.style.zIndex = 0)
      document.querySelectorAll("ul.sidemenu-nav a").forEach((el) => {
        if (el.classList.contains("activated")) {
          el.classList.remove("activated");
        }
        e.target.classList.add("activated");
      });
    },
  },
  mounted() {
    gsap
      .timeline({
        scrollTrigger: {
          trigger: ".how__supdescription",
          start: "center bottom",
          end: "bottom",
          toggleActions: "restart none none none",
          // scrub: true,
          // pin: true,
        },
      })
      .fromTo(
        ".suptitle",
        { y: 30, opacity: 0, duration: 2 },
        { y: 0, opacity: 1 }
      )
      .fromTo(
        ".supdesription",
        { y: 30, opacity: 0, duration: 2 },
        { opacity: 1, y: 0 }
      );

    gsap.to(".illustration-image", {
      x: 0,
      duration: 2,
      scrollTrigger: {
        trigger: ".sidemenu-nav",
        start: "top center",
        toggleActions: "restart none none reverse",
      },
    });

    gsap.fromTo(
      ".sidemenu",
      { x: "-360px", y: -100 },
      {
        scrollTrigger: {
          trigger: ".sidemenu-nav",
          start: "top center",
          toggleActions: "restart none none reverse",
        },
        opacity: 1,
        x: 0,
        y: 0,
        duration: 2,
      }
    );

    const tl = gsap.timeline();
    tl.to(".point", {
      scrollTrigger: {
        trigger: ".how__illustration",
        start: "80% bottom",
        toggleActions: "play none none reverse",
      },
      display: "block",
    });
  },
};
</script>

<style scoped>
.how__supdescription {
  display: flex;
  justify-content: space-evenly;
  text-align: start;
}

.suptitle,
.supdescription {
  flex: 0 0 50%;
}
.supdesription {
  max-width: 410px;
}

.how__illustration {
  display: flex;
  justify-content: center;
  margin-top: 50px;
  height: 800px;
  overflow: hidden;
}
.sidemenu {
  flex: 1 1 25%;
  display: flex;
  flex-direction: column;
  background-color: #5a30f0;
  padding: 35px 50px;
  text-align: start;

  color: #fff;
}
.sidemenu-nav {
  font-weight: 400;
  margin: auto 0;
}
.sidemenu-nav li {
  position: relative;
  cursor: pointer;
}
.sidemenu-nav li a {
  font-weight: 400;
  font-size: 44px;
  line-height: 53px;
  color: #fff;
  opacity: 0.7;
  margin-left: 20px;
  transition: opacity 1s linear;
}
.sidemenu-nav li:hover a,
.sidemenu-nav li a.activated {
  font-style: italic;
  opacity: 1;
  transition: opacity 0.2s linear;
}
.sidemenu-nav li a.activated::before {
  content: "\2192";
  position: absolute;
  top: 25%;
  left: -10px;
  font-size: 30px;
  line-height: 10px;
}

.illustration-image {
  transform: translateX(-180px);
  width: 200%;
}

.img-cont {
  width: 100%;
  height: 100%;
  position: relative;
}

.image-1 {
  background: url("../assets/img/illustration-bg.png") 0 0 no-repeat;
}

.image-2 {
  background: url("../assets/img/illustration-bath-bg.png") 0 0 no-repeat;
}

.point {
  display: none;
  position: absolute;
  font-size: 30px;
  line-height: 0;
  color: #fff;
  background-color: #5a30f0;
  width: 30px;
  height: 30px;
  border-radius: 50%;
}
.point:hover {
  box-shadow: 0 0 20px #5a30f0;
}
.point1 {
  top: 250px;
  left: 320px;
}
.point2 {
  top: 445px;
  left: 262px;
}
.point3 {
  top: 715px;
  left: 300px;
}
.point4 {
  top: 475px;
  left: 470px;
}
.point5 {
  top: 377px;
  left: 631px;
}
.point6 {
  top: 586px;
  left: 591px;
}
.point7 {
  top: 497px;
  left: 831px;
}

@media (max-width: 768px) {
  .how__illustration {
    flex-wrap: wrap;
    height: 1100px;
  }

  .illustration-image {
    height: 100%;
  }

  .img-cont {
    background-position-x: 50%;
  }
}
</style>