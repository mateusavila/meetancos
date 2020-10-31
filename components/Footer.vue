<template>
  <footer>
    <div class="container-footer">
      <p>Pode copiar o conteúdo.</p>
    </div>
  </footer>
</template>
<script lang="ts">
  import Vue, { PropOptions } from 'vue'
  export default Vue.extend({
    name: 'Footer'
  })
</script>
<style lang="stylus">
  footer
    display block
    width 100%
    height 80px
    background #454545
    z-index 100
    p
      color #fafafa
      margin 0
      line-height 1
      font-size 14px
  .container-footer
    width calc(100% - 40px)
    margin 0 auto
    display flex
    align-items center
    height 100%
  @media all and (max-width: 600px)
    .container-footer
      width calc(100% - 20px)
</style>