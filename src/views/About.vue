<template>
  <div class="about">
    <h1>{{ state.message }}</h1>
  </div>
</template>

<script>
import { reactive } from "vue";
export default {
  setup() {
    const state = reactive({
      message: "This is an Design Page"
    });
    return {
      state
    };
  }
};
</script>
