<template>
  <div id="carouselExampleControls" class="carousel slide" data-bs-ride="carousel">
    <div class="carousel">
      <img :src="images[currentIndex]" alt="Carousel Image" />
    </div>
  </div>
</template>

<script>
import { ref, onMounted, onBeforeUnmount } from 'vue';

export default {
  name: 'Carousel',
  setup() {
    const images = ref([
      '/public/sliders/slider_1.png',
      '/public/sliders/slider_2.png',
      '/public/sliders/slider_3.png',
      '/public/sliders/slider_4.png',
      '/public/sliders/slider_5.png'
    ]);

    const currentIndex = ref(0);
    let intervalId = null;

    onMounted(() => {
      intervalId = setInterval(() => {
        currentIndex.value = (currentIndex.value + 1) % images.value.length;
      }, 3000);
    });

    onBeforeUnmount(() => {
      clearInterval(intervalId);
    });

    return { images, currentIndex };
  }
};
</script>

<style scoped>

.carousel{
  height: 800px;
  width: 1200px;
  overflow: hidden;
}

.carousel-control-prev{
  padding-bottom: 200px;
  color: aqua;
}
.carousel-control-next{
  padding-bottom: 200px;
  color: aqua;
}
img{
  height: 500px;
  width: 1200px;
}
</style>
