<template>
  <div id="app">
    <Header />
    <transition name="fade" mode="out-in">
      <router-view />
    </transition>
    <Footer />
  </div>
</template>

<script>
import Header from "./components/Header";
import Footer from "./components/Footer";
export default {
  components: {
    Header,
    Footer
  }
};
</script>

<style lang="sass">

body
  background: #f2f3f7

#app
  font-family: Avenir, Helvetica, Arial, sans-serif
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  text-align: center
  color: #2c3e50

.fade-enter-from,
.fade-leave-to
  opacity: 0
.fade-enter-active,
.fade-leave-active
  transition: opacity 1s
</style>
