<template lang="pug">
div#app.h-100
  Home(msg="Welcome")
</template>

<script>
import Home from './views/Home.vue'

export default {
  name: 'App',
  components: {
    Home
  }
}
</script>

<style lang="scss">
</style>
