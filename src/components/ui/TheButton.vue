<template>
  <button class="annoying-button" @mouseover="btnActivity">
    Заказать<br />уборку
  </button>
</template>

<script>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

export default {
  methods: {
    buttonMes() {
      const btnAnim = gsap.timeline({
        defaults: { duration: 5 },
        repeat: -1,
      });
      btnAnim
        .to(".annoying-button", { rotation: 90 })
        .to(".annoying-button", { rotation: -90 })
        .to(".annoying-button", { rotation: 0 });
      return btnAnim;
    },
    btnActivity(event) {
      gsap.to(".annoying-button", {
        y: 0,
        duration: 1,
      });
      console.log(event)
      console.log(event.target.getBoundingClientRect())
      
      // var boxElem = document.querySelector(".annoying-button");
      // var pointerElem = document.querySelector(".annoying-button");

      // function onMouseMove(event) {
      //   console.log()
      //   var mouseX = event.pageX;
      //   var mouseY = event.pageY;
      //   var crd = boxElem.getBoundingClientRect();
      //   var activePointer =
      //     crd.left <= mouseX &&
      //     mouseX <= crd.right &&
      //     crd.top <= mouseY &&
      //     mouseY <= crd.bottom;

      //   requestAnimationFrame(function movePointer() {
      //     if (activePointer) {
      //       pointerElem.classList.remove("box-pointer-hidden");
      //       pointerElem.style.left = Math.floor(mouseX) + "px";
      //       pointerElem.style.bottom = Math.floor(mouseY) + "px";
      //     } else {
      //       pointerElem.classList.add("box-pointer-hidden");
      //     }
      //   });
      // }

      // function disablePointer() {
      //   pointerElem.style.left = "83px";
      //   pointerElem.style.bottom = "83px";
      //   requestAnimationFrame(function hidePointer() {
      //     pointerElem.classList.add("box-pointer-hidden");
      //   });
      // }

      // boxElem.addEventListener("mousemove", onMouseMove, false);
      // pointerElem.addEventListener("mouseleave", disablePointer, false);
    },
  },
  mounted() {
    // const t1 = gsap.timeline({defaults: {duration: 2}});
    // t1.fromTo(".annoying-button", {
    //   y: 0,
    // }, {
    //   scrollTrigger: {
    //     trigger: ".hero",
    //     start: `${document.querySelector(".hero").offsetHeight / 5}`
    //   },
    //   y: 50
    // })
    // .add(this.buttonMes)
    this.buttonMes();
    gsap.fromTo(
      ".annoying-button",
      {
        y: 80,
        duration: 1,
      },
      {
        scrollTrigger: {
          trigger: ".how__illustration",
          start: "top 60%",
          toggleActions: "restart none none reverse",
          scrub: true
        },
        x: -100,
        y: 500,
        duration: 1,
      }
    );
  },
};
</script>

<style scoped>
.annoying-button {
  position: fixed;
  left: 50%;
  bottom: 50px;
  width: 180px;
  height: 180px;
  background-color: #5a30f0;
  border-radius: 50%;
  font-weight: 700;
  font-size: 16px;
  line-height: 21px;
  z-index: 300;
  letter-spacing: 0.03em;
  text-transform: uppercase;

  /* White */

  color: #ffffff;
}
</style>