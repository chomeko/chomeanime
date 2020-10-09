<template>
  <div class="footer">
    <dl>
      <dt>ちょめこ</dt>
      <dd><a href="https://twitter.com/chomeko3o" rel="noopener" target="_blank">Twitter</a></dd>
    </dl>
    <Lottie
    :options="Twitter"
    :height="100"
    :width="100"
    :animCreated="handleAnimation"
  />
  </div>
</template>

<script>
import { reactive, computed } from "vue";
import Lottie from "../components/Lottie";
// アニメーション
import * as twitter from "../assets/twitte.json";

export default {
  components: {
    Lottie
  },
  setup() {
    const state = reactive({
      anim: ""
    });

    const handleAnimation = anim => {
      state.anim = anim;
    };

    const Twitter = computed(() => ({
      animationData: twitter,
      loop: true
    }));

    return {
      state,
      handleAnimation,
      Twitter
    };
  }
};
</script>

<style lang="sass" scoped>
.footer
  dl
    display: flex
    justify-content: center
    align-items: center
  dt
    font-weight: bold
    font-size: 24px
  dd
    letter-spacing: 1px
    font-size: 20px
    a
      color: #00A7FF
</style>