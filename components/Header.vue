<template>
  <header>
    <div class="container-header">
      <p>Palestra | Meetanços <br><small>Vue JS</small></p>
    </div>
  </header>
</template>
<script lang="ts">
  import Vue, { PropOptions } from 'vue'
  export default Vue.extend({
    name: 'Header'
  })
</script>
<style lang="stylus">
  header
    position fixed
    top 0
    left 0
    width 100%
    height 70px
    background #35495E
    z-index 100
    p
      color #fafafa
      margin 0
      line-height 1
      font-size 22px
      small
        font-weight normal
        font-size 16px
  .container-header
    width calc(100% - 40px)
    margin 0 auto
    display flex
    align-items center
    height 100%
  @media all and (max-width: 600px)
    .container-header
      width calc(100% - 20px)
</style>