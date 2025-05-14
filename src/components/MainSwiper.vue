<template>
  <swiper
      :modules="[Autoplay]"
      :loop="true"
      direction="vertical"
      :autoplay="{ delay: 2000, disableOnInteraction: false }"
      class="my-swiper"
  >
    <swiper-slide v-for="(card, index) in cards" :key="index">
      <div class="card">
        <h3>{{ card.title }}</h3>
        <p>{{ card.description }}</p>
      </div>
    </swiper-slide>
  </swiper>
</template>

<script>
import { Swiper, SwiperSlide } from 'swiper/vue';
import { Autoplay } from 'swiper/modules';
import 'swiper/css';

export default {
  components: {
    Swiper,
    SwiperSlide
  },
  setup() {
    const cards = [
      { title: 'Карточка 1', description: 'Описание 1' },
      { title: 'Карточка 2', description: 'Описание 2' },
      { title: 'Карточка 3', description: 'Описание 3' },
      { title: 'Карточка 4', description: 'Описание 4' },
    ];

    return {
      cards,
      Autoplay
    };
  }
};
</script>

<style scoped>
.my-swiper {
  height: 90vh;
  width: 100%;
}

.card {
  height: 100%;
  background: #444;
  color: white;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
