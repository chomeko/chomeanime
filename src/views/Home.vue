<template>
  <div class="home">
    <Lottie
      :options="LoveHand"
      :height="150"
      :width="200"
      :animCreated="handleAnimation"
    />
    <Title :msg="state.message" />

    <div class="myMessage">
      <p>このサイトはvue初学者の僕が、Illustrator AfterEffect Lottieを
        使ったデザインを投稿するサイトである。<br>
        あなたがLottieを使えるのならば、使ってくれてかまわない。
        気に入ったデザインがあれば気軽に言ってほしい。
      </p>
    </div>
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
      LoveHand,
    };
  }
};
</script>

<style lang="sass" scoped>
$breakpoints: ('sp': 'screen and (min-width: 400px)','pc': 'screen and (min-width: 768px)')
=mq($breakpoint: sp)
  @media #{map-get($breakpoints, $breakpoint)}
    @content

.home
  padding: 30px
.myMessage
  line-height: 2
  font-size: 12px
  +mq(pc)
    font-size: 14px
</style>
