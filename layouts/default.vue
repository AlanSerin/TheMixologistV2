<template>
  <div class="page-container">
    <div class="position-absolute w-100 h-100" style="z-index: -1;background-color: black">
      <div class="bg-image"></div>
    </div>
    <Header />
    <Nuxt class="nuxt-padding" />
  </div>
</template>

<script>
export default {
  name: "default"
}
</script>

<style scoped>
@media only screen and (min-width: 750px) {
  .nuxt-padding {
    padding: 2rem;
  }
}

.page-container {
  height: 100vh;
  width: 100vw;
  background: transparent;
  display: flex;
  flex-direction: column;
  overflow-y: auto;
  overflow-x: hidden;
}
.page-container::-webkit-scrollbar {
  display: none;
}

/* Hide scrollbar for IE, Edge and Firefox */
.page-container {
  -ms-overflow-style: none;  /* IE and Edge */
  scrollbar-width: none;  /* Firefox */
}
.bg-image {
  background-image: url(~static/images/barr.png);
  filter: blur(6px) brightness(0.6);
  -webkit-filter: blur(6px) brightness(0.6);
  height: 100%;
  width: 100%;
}
</style>
