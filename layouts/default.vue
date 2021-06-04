<template>
  <div :style="{ backgroundImage: `url(${background_img})` }">
    <AppHeader />
    <div class="mt-20 mb-10 h-full container mx-auto">
      <Nuxt />
    </div>
    <AppFooter />
  </div>
</template>

<script>
import backgroundImg from "assets/background.png";
export default {
  data() {
    return {
      items: [],
      background_img: backgroundImg
    }
  },
}
</script>