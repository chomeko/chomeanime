<template>
  <div class="home">
    <Lottie :options="LoveHand" :height="150" :width="200" :animCreated="handleAnimation" />
    <Title msg="Welcome to Chomeko Design`s" />
  </div>
</template>

<script>
// @ is an alias to /src
import Title from "../components/Title";
import Lottie from "../components/Lottie";
// アニメーション
import * as loveHand from "../assets/love-hand.json";

export default {
  name: "Home",
  components: {
    Title,
    Lottie,
  },
  computed: {
    LoveHand() {
      return { animationData: loveHand, loop: true };
    }
  },
  methods: {
    handleAnimation(anim) {
      this.anim = anim;
    }
  }
};
</script>
