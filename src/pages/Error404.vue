<template>
  <q-layout>
    <q-page-container
      class="container text-white fullscreen text-center q-pa-md flex flex-center"
    >
      <q-page>
        <div style="font-size: 5vh">
          🚀 404
        </div>

        <div class="text-h5" style="opacity:.4">
          Perdidos en el espacio...
        </div>

        <lottie
          :options="defaultOptions"
          :height="600"
          :width="600"
          v-on:animCreated="handleAnimation"
        />
      </q-page>

      <!-- Stycky Button Star -->
      <q-page-sticky position="top-right" :offset="[18, 18]">
        <q-fab icon="help" direction="down" color="yellow-6" outline>
          <q-fab-action
            v-for="link in buttonsLinks"
            :key="link.link"
            @click="onClick(link.link)"
            color="deep-orange-4"
            :icon="link.icon"
            outline
          />
        </q-fab>
      </q-page-sticky>
      <!-- Stycky Button End -->
    </q-page-container>
  </q-layout>
</template>

<script>
import Lottie from "../components/lottie";
// import * as animationData from "../assets/woman.json";
import * as animationData from "../assets/astrolottie.json";

import { linksData } from "../components/Links";

export default {
  name: "Error404",

  components: {
    lottie: Lottie
  },

  data() {
    return {
      defaultOptions: { animationData: animationData.default },
      animationSpeed: 2,
      buttonsLinks: [
        {
          icon: "home",
          link: "/"
        }
      ]
    };
  },

  mounted() {
    linksData.map(link => {
      // console.log(link, link.icon, link.link);
      this.buttonsLinks.push({ icon: link.icon, link: link.link });
    });
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
    },

    onClick(link) {
      if (link.indexOf("http") === -1) {
        this.$router.push(link);
      } else {
        window.open(link, "_blank");
      }
      // this.$router.push("/");
    }
  }
};
</script>
<style lang="scss" scoped>
.container {
  background: #000c0f;
}
</style>
