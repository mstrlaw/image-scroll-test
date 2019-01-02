<template>
  <Layout>
    <div class="img-test">
      <b>Regular:</b>
      <g-image
        alt="Example image"
        src="~/favicon.png" width="135"
      />
    </div>
    <div class="img-test">
      <b>With&nbsp;<em>immediate</em>:</b>
      <g-image
        alt="Example image"
        src="~/favicon.png" width="135"
        immediate=true
      />
    </div>
    <div
      class="h-100"
      :style="{ transform: 'translateY('+yPos+'px)' }"
    >
      <p>Big height for scroll</p>
    </div>
  </Layout>
</template>

<script>
export default {
  data(){
    return {
      yPos: 0,
    }
  },
  beforeMount(){
    window.addEventListener('scroll', this.applyParallax)
  },
  beforeDestroy(){
    window.removeEventListener('scroll', this.applyParallax)
  },
  methods:{
    applyParallax(){
      this.yPos = window.scrollY * 0.1
    }
  }
}
</script>

<style>
  .img-test{
    display: flex;
    align-items: center;
    width: 100%;
    margin: 50px 0;
  }
  b{
    min-width: 150px;
  }
  .h-100{
    height: 100vh;
  }
</style>
