<template>
  <div class="todo">
    <h4>{{ todo.title }}</h4>
    <img :src="todo.image" alt="todo-img" />
    <div class="overlay-info">
      Не нужно тратить время, силы и ресурсы на разме- щение вакансий, проведе-
      ние собеседований, про- верку кандидатов на должность уборщицы. За счет
      больших объемов мы можем сделать это эффективнее.
    </div>
  </div>
</template>

<script>
import { gsap } from "gsap";

export default {
  props: {
    todo: {
      type: Object,
      required: false,
    },
  },
  mounted() {   
    gsap.fromTo(".todo", {opacity: 0, y: 30, duration: 2}, {opacity: 1, y: 0, stagger: .5})
  }
};
</script>

<style scoped>
.todo {
  width: 100%;
  max-width: 300px;
  height: 330px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  text-align: center;
  border-radius: 8px;
  background: #f3f6fb;
  padding: 20px 15px 0 15px;
  position: relative;
  z-index: 10;
}

.overlay-info {
  position: absolute;
  top: 0px;
  height: 330px;
  background: #5A30F0;
  padding: 30px;
  border-radius: 8px;
  opacity: 0;
  z-index: 50;
  color: #fff;
  text-align: start;
  transition: opacity 0.3s ease-out;
}

.todo:hover .overlay-info {
  opacity: 1;
  transition: opacity 0.3s ease-in;
}
</style>