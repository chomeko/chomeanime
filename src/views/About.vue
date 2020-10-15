<template>
  <div id="about">
    <h1>{{ state.message }}</h1>
    <div v-for="(design, index) in state.designs" :key="index">
      <div class="designs">
        <Lottie
          :options="Design(design.animationData)"
          :height="150"
          :width="200"
          @anim-created="handleAnimation($event, index)"
        />
      </div>
      <span class="designs__Name">{{ design.name }}</span>
        <div class="designs__Btn">
          <Button v-if="design.isActive" @button="play($event, index)" type="aboutBtn" key="start">再生</Button>
          <Button v-if="!design.isActive" @button="stop($event, index)" type="aboutBtn2" key="stop">停止</Button>
        </div>
    </div>
  </div>
</template>

<script>
import { reactive, computed } from "vue";
import Lottie from "../components/Lottie";
//lottieアニメーションデータ
import * as loveHand from "../assets/love-hand.json";
import * as twitter from "../assets/twitte.json";
//button
import Button from "../components/Button"

export default {
  name: "about",
  components: {
    Lottie,
    Button
  },
  setup() {
    const state = reactive({
      message: "This is an Design Page",
      designs: [
        {
          name: "loveHand",
          animationData: loveHand,
          anim: "",
          isActive: true
        },
        {
          name: "twitter",
          animationData: twitter,
          anim: "",
          isActive: true
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

    const stop = (event, index) => {
      state.designs[index].anim.stop();
      state.designs[index].isActive = true
    };

    const play = (event, index) => {
      state.designs[index].anim.play(event);
      state.designs[index].isActive = false
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

<style lang="sass" scoped>
.designs
  margin-top: 24px
  &__Name
    font-size: 20px
    font-weight: bold
  &__Btn
    display: flex
    justify-content: center
    margin: 5px
</style>
