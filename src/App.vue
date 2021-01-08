<template>
  <div>
    <ResponsiveNav
      :image-path="require('./assets/logo.png')"
      background="#000"
     />

      <!--
     <ResponsiveNavTailwind
      :image-path="require('./assets/logo.png')"
      
      /> -->

  </div>
</template>

<script>
  import ResponsiveNav from "./components/navbar/ResponsiveNav"
  // import ResponsiveNavTailwind from "./components/navbar/ResponsiveNavTailwind"
  export default {
    components: {
      ResponsiveNav
      // ResponsiveNavTailwind
    }
  }
</script>

<style>

</style>
