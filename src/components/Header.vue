<template>
  <div id="header">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </div>
</template>

<style lang="sass" scoped>
#header
  padding: 30px

  a
    font-weight: bold
    color: #2c3e50

    &.router-link-exact-active
      color: #fb1967
      font-size: 20px
</style>
