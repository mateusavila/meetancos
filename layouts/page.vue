<template>
  <div class="page">
    <Header />
    <main>
      <Nuxt />
    </main>
    <Footer />
  </div>
</template>
<script lang="ts">
  const Header = () => import('~/components/Header.vue')
  const Footer = () => import('~/components/Footer.vue')
  import Vue, { PropOptions } from 'vue'
  export default Vue.extend({
    name: 'page',
    components: {
      Header, Footer
    }  
  })
</script>

<style lang="stylus">
html
  -ms-text-size-adjust: 100%
  -webkit-text-size-adjust: 100%
  -moz-osx-font-smoothing: grayscale
  -webkit-font-smoothing: antialiased
  box-sizing: border-box
  background #fefefe
  font-family: 'Roboto', sans-serif
body
  font-family: 'Roboto', sans-serif
*, *::before, *::after
  box-sizing: border-box
.container
  width 1000px
  margin 0 auto
main
  min-height: 1000px
@media all and (max-width: 1050px)
  .container
    width calc(100% - 40px)
@media all and (max-width: 600px)
  .container
    width calc(100% - 20px)
</style>
