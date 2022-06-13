<template>
  <div class="flex items-center">
    <div class="w-490px flex-grow-0">
      <div
        id="photo"
        class="bg-center bg-white bg-cover bg-no-repeat pb-150 shadow"
      ></div>
    </div>
    <div v-mouse-move class="flex-1 pl-8 pt-16">
      <h1
        class="text-black uppercase font-extrabold text-4xl leading-none mb-5"
      >
        {{ firstName }}
        <div class="relative">
          <div
            class="absolute w-120px right-100 top-50 border-blue border-b-5 line-transform"
          ></div>
          <span class="text-blue">{{ lastName }}</span>
        </div>
      </h1>
      <h2 class="mb-2">{{ position }}</h2>
      <p class="text-gray">
        Sou louco por tecnologia e minha inspiração é desenvolver soluções.
        <br />
        {{ aboutMe }} &rarr;
        <a href="/contact" class="link--styled">Entre em contato</a>
      </p>
    </div>
  </div>
</template>

<script>
import { getAge } from "~/utils/functions";
import { mouseMove } from "~/utils/directives";
import {
  firstName,
  lastName,
  position,
  birthday,
  aboutMe,
} from "~/docs/profile.json";

export default {
  directives: {
    mouseMove,
  },

  data() {
    return {
      firstName,
      lastName,
      position,
      aboutMe,
    };
  },

  computed: {
    age() {
      return getAge(birthday);
    },
  },
};
</script>

<style scoped>
.line-transform {
  transform: translate(-25px, -50%);
}
#photo {
  background-image: url("~assets/images/elbercosta.jpeg");
}
.link--styled {
  color: #4c33fb;
  position: relative;
  -webkit-transition: color 0.25s;
  transition: color 0.25s;
}
.link--styled:hover {
  content: "";
  top: 100%;
  left: 0;
  width: 100%;
  -webkit-transform: translateY(-12px);
  transform: translateY(-12px);
  opacity: 0.2;
  border-bottom: 3px solid #4c33fb;
  -webkit-transition: transform 0.25s, opacity 0.25s;
  transition: transform 0.25s, opacity 0.25s;
}
</style>
