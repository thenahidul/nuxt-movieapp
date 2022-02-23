<template>
  <div
    class="d-flex align-center hero"
    :style="{ backgroundImage: `url(${herobg})` }"
  >
    <div class="container">
      <div>
        <span class="mini-heading">Now Stremaing</span>
        <h1><span>Now</span> Streaming</h1>
      </div>
    </div>
  </div>
</template>

<script>
import HeroImage from '~/assets/images/banner1.jpg'
export default {
  name: 'Hero',
  data() {
    return {
      herobg: HeroImage,
    }
  },
}
</script>

<style lang="scss" scoped>
.hero {
  min-height: 500px;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center center;
  background-attachment: fixed;
  @media (max-width: 767px) {
    min-height: 300px;
  }
}
.mini-heading {
  text-transform: uppercase;
  color: crimson;
  font-weight: 600;
  font-size: 24px;
}
h1 {
  font-size: 5rem;
  margin: 10px 0;
  @media (max-width: 767px) {
    font-size: 3rem;
    line-height: 1.2;
  }
}
</style>
