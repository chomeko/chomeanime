<template>
  <div :style="state.style" ref="lavContainer"></div>
</template>

<script>
import { reactive, onMounted, ref } from "vue";
import lottie from "lottie-web";

export default {
  props: {
    options: {
      type: Object,
      required: true
    },
    height: Number,
    width: Number
  },
  setup(props,context) {
    const state = reactive({
      style: {
        width: props.width ? `${props.width}px` : "100%",
        height: props.height ? `${props.height}px` : "100%",
        overflow: "hidden",
        margin: "0 auto"
      }
    });

    const lavContainer = ref(null);

    onMounted(() => {
      const LottieAnim = lottie.loadAnimation({
        container: lavContainer.value,
        renderer: "svg",
        loop: props.options.loop,
        autoplay: props.options.autoplay !== false,
        animationData: props.options.animationData.default,
        rendererSettings: props.options.rendererSettings,
      });
      context.emit('anim-created', LottieAnim)
    });

    return {
      state,
      lavContainer
    };
  }
};
</script>
