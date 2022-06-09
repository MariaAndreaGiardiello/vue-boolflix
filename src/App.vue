<template>
  <div id="app">
    <HeaderComponents/>
    <MainComponents/>
    <FooterComponents/>
  </div>
</template>

<script>
import HeaderComponents from '../src/components/HeaderComponents.vue'
import MainComponents from '../src/components/MainComponents.vue'
import FooterComponents from '../src/components/FooterComponents.vue'

export default {
  name: 'App',
  components: {
    HeaderComponents,
    MainComponents,
    FooterComponents,
  }
}
</script>

<style lang="scss">
</style>
