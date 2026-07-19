<script setup>
import { inject } from 'vue';
import CardPonto from '../components/CardPonto.vue';

const pontos = inject("pontos");
</script>

<template>
  <section>
    <h1>Pontos de Interesse</h1>
    <div class="galeria">
      <CardPonto v-for="p in pontos" :key="p.id" :ponto="p" />
    </div>
  </section>
</template>

<style scoped>
.galeria {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
  gap: 20px;
  padding: 20px;
}
</style>