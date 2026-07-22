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
  /* Título */
  h1 {
    font-size: 28px;
    margin: 30px 0 20px;
    text-align: center;
    color: #7a7a7a;
  }

  /* Galeria base */
  .galeria {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    gap: 24px;
    padding: 20px;
    max-width: 1400px;   /* limite elegante */
    margin: 0 auto;      /* centraliza em telas grandes */
  }

  /* Tablets */
  @media (max-width: 1024px) {
    .galeria {
      grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
      max-width: 100%;
    }

    h1 {
      font-size: 24px;
    }
  }

  /* Celulares grandes */
  @media (max-width: 768px) {
    .galeria {
      grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
      gap: 18px;
    }

    h1 {
      font-size: 22px;
    }
  }

  /* Celulares pequenos */
  @media (max-width: 480px) {
    .galeria {
      grid-template-columns: 1fr;
      padding: 12px;
      gap: 16px;
    }

    h1 {
      font-size: 20px;
    }
  }

  /* Notebooks grandes */
  @media (min-width: 1280px) {
    .galeria {
      max-width: 1500px;
      grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    }
  }
</style>