<template>
  <div class="about">
    <h1>{{ state.message }}</h1>
    <div v-for="(design, index) in state.designs" :key="index">
      <div>
        <Lottie
          :options="Design(design.animationData)"
          :height="150"
          :width="200"
          @anim-created="handleAnimation($event, index)"
        />
      </div>
      {{ design.name }}
      <button @click="play(index)">再生</button>
      <button @click="stop(index)">停止</button>
    </div>
  </div>
</template>

<script>
import { reactive, computed } from "vue";
import Lottie from "../components/Lottie";
//lottieアニメーションデータ
import * as loveHand from "../assets/love-hand.json";
import * as twitter from "../assets/twitte.json";

export default {
  name: "about",
  components: {
    Lottie
  },
  setup() {
    const state = reactive({
      message: "This is an Design Page",
      designs: [
        {
          name: "loveHand",
          animationData: loveHand,
          anim: ""
        },
        {
          name: "twitter",
          animationData: twitter,
          anim: ""
        }
      ]
    });

    const handleAnimation = (event, index) => (
      state.designs[index].anim = event
      //console.log(state.designs[index])
    );

    const Design = computed(() => data => ({
      animationData: data,
      loop: true,
      autoplay: false
    }));

    const stop = (index) => {
        state.designs[index].anim.stop();
    };

    const play = (index) => {
      state.designs[index].anim.play();
      //console.log(state.designs[index].anim)
    };

    return {
      state,
      handleAnimation,
      Design,
      stop,
      play
    };
  }
};
</script>
