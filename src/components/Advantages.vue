<template>
  <div class="container">
    <section class="advantages">
      <WhatWeDo v-for="todo in workList" :key="todo.id" :todo="todo" :class="'todo' + todo.id"/>
    </section>
  </div>
</template>

<script>
import WhatWeDo from "@/components/WhatWeDo.vue";

export default {
  data() {
    return {
      workList: [
        {
          id: 1,
          title: "Тщательно отобранный персонал",
          image: require("../assets/img/icon-advantages-1.svg"),
        },
        {
          id: 2,
          title: "Качественная эко-химия",
          image: require("../assets/img/icon-advantages-2.svg"),
        },
        {
          id: 3,
          title: "Контролируем качество",
          image: require("../assets/img/icon-advantages-3.svg"),
        },
        {
          id: 4,
          title: "Работаем круглосуточно",
          image: require("../assets/img/icon-advantages-4.svg"),
        },
      ],
    };
  },
  components: {
    WhatWeDo,
  },
};
</script>

<style scoped>
.advantages {
  display: flex;
  justify-content: center;
  margin-top: 70px;
  margin-bottom: 150px;
  column-gap: 30px;
  row-gap: 30px;
}

@media (max-width: 1150px) {
  .advantages {
    flex-wrap: wrap;
  }
}
</style>