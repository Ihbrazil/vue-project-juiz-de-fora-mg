<script setup>
    import { inject, ref, computed } from 'vue';
    import CardPonto from '../components/CardPonto.vue';
    const pontos = inject("pontos");
    const categoriaSelecionada = ref("Parques");

    const categorias = computed(() => [...new Set(pontos.value.map(p => p.categoria))]);
    const filtrados = computed(() => pontos.value.filter(p => p.categoria === categoriaSelecionada.value));
</script>

<template>
  <h1>Categorias</h1>
  <select v-model="categoriaSelecionada">
    <option v-for="c in categorias" :key="c">{{ c }}</option>
  </select>
  <div class="galeria">
    <CardPonto v-for="p in filtrados" :key="p.id" :ponto="p" />
  </div>
</template>

<style scoped>
  /* Título */
  h1 {
    font-size: 28px;
    margin: 30px 0 20px;
    text-align: center;
    color: #7a7a7a;
  }

  /* Select */
  select {
    display: block;
    margin: 0 auto 25px;
    padding: 12px 16px;
    font-size: 16px;
    border-radius: 8px;
    border: 1px solid #ccc;
    background: #fff;
    cursor: pointer;
    transition: 0.2s;
    width: 320px;              /* largura ideal */
    max-width: 90%;            /* evita quebrar em telas pequenas */
  }

  select:hover {
    border-color: #4a90e2;
  }

  /* Galeria */
  .galeria {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    gap: 24px;
    padding: 20px;
    max-width: 1400px;         /* limite elegante */
    margin: 0 auto;            /* centraliza */
  }

  /* Tablets */
  @media (max-width: 1024px) {
    select {
      width: 70%;
      font-size: 15px;
    }

    .galeria {
      grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
    }

    h1 {
      font-size: 24px;
    }
  }

  /* Celulares grandes */
  @media (max-width: 768px) {
    select {
      width: 85%;
      font-size: 15px;
      padding: 10px 14px;
    }

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
    select {
      width: 100%;
      font-size: 14px;
      padding: 8px 12px;
    }

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
    select {
      width: 360px;
      font-size: 17px;
    }

    .galeria {
      max-width: 1500px;
      grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    }
  }
</style>