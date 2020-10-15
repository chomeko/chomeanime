<template>
  <div>
    <button
      class="myButton"
      :class="type"
      @click="ButtonEmit"
    >
    <slot/>
    </button>
  </div>
</template>

<script>

export default {
  props: {
    type: {
      type: String,
      required: true
    }
  },
  setup(props, context) {

    const ButtonEmit = () => {
      context.emit('button')
    }

    return {
      ButtonEmit
    }
  }
}
</script>

<style lang="sass" scoped>

$bg-color: #f2f3f7
$color-strat: #8a00f1
$color-stop: #ff8607

.myButton
  cursor: pointer
  outline: none
  border: none
  font-weight: bold
  border-radius: 5px
  box-shadow: -6px -6px 14px rgba(255, 255, 255, .7), -6px -6px 10px rgba(255, 255, 255, .5), 6px 6px 8px rgba(255, 255, 255, .075), 6px 6px 10px rgba(0, 0, 0, .15)

.aboutBtn
  background: $bg-color
  color: $color-strat
  padding: 10px 10px
  margin: 0 5px 0 5px
  &:hover
    box-shadow: -2px -2px 4px 0px #ffffff, 3px 3px 3px 0px rgba(0, 0, 0, .15)
    transition: .5s

.aboutBtn2
  background: $bg-color
  color: $color-stop
  padding: 10px 10px
  margin: 0 5px 0 5px
  box-shadow: -2px -2px 4px 0px #ffffff, 3px 3px 3px 0px rgba(0, 0, 0, .15)
  transition: .5s
</style>