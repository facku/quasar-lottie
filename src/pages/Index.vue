<template>
  <q-page padding>
    <div class="row">
      <div class="col-12 col-md-6 flex justify-center flex-center">
        <div class="text-h2 text-lime-2">
          Quasar & Lottie
          <q-btn
            icon-right="chevron_right"
            label="Pagina 404"
            flat
            class="text-lime-6"
            @click="$router.push('/omg')"
          ></q-btn>
        </div>
      </div>
      <div class="col-12 col-md-6 flex flex-center">
        <lottie :options="defaultOptions" v-on:animCreated="handleAnimation" />
      </div>
    </div>
  </q-page>
</template>

<script>
import Lottie from "../components/lottie";
// import * as animationData from "../assets/woman.json";
import * as animationData from "../assets/lottie.json";

export default {
  name: "PageIndex",

  components: {
    lottie: Lottie
  },

  data() {
    return {
      defaultOptions: { animationData: animationData.default },
      animationSpeed: 2
    };
  },

  methods: {
    handleAnimation: function(anim) {
      this.anim = anim;
    },
    stop: function() {
      this.anim.stop();
    },
    play: function() {
      this.anim.play();
    },
    pause: function() {
      this.anim.pause();
    },
    onSpeedChange: function() {
      this.anim.setSpeed(this.animationSpeed);
    }
  }
};
</script>
<style lang="scss" scoped>
.q-page {
  background: transparent;
  position: relative;
  &::after {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    background: rgb(0, 140, 255);
    width: 100%;
    height: 100%;
    z-index: -2;
    clip-path: polygon(50% 0%, 100% 0, 100% 100%, 0 99%, 0 33%);
  }
  &::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    background: rgb(234, 0, 255);
    width: 100%;
    height: 100%;
    z-index: -1;
    opacity: 0.25;
    clip-path: polygon(100% 0, 0% 100%, 100% 100%);
  }
}
</style>
