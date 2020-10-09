<template>
  <div class="home">
    <Lottie
      :options="LoveHand"
      :height="150"
      :width="200"
      :animCreated="handleAnimation"
    />
    <Title :msg="state.message" />
  </div>
</template>

<script>
// @ is an alias to /src
import { reactive, computed } from "vue";
import Title from "../components/Title";
import Lottie from "../components/Lottie";
// アニメーション
import * as loveHand from "../assets/love-hand.json";

export default {
  name: "Home",
  components: {
    Title,
    Lottie
  },
  setup() {
    const state = reactive({
      message: "Welcome to Chomeko Design`s",
      anim: ""
    });

    const handleAnimation = anim => {
      state.anim = anim;
    };

    const LoveHand = computed(() => ({
      animationData: loveHand,
      loop: true
    }));

    return {
      state,
      handleAnimation,
      LoveHand
    };
  }
};
</script>
