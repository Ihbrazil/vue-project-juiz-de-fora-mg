<script setup>
  import { ref, provide } from 'vue';
  import pontosData from "@/assets/pontos_turisticos.json";
  import HomePage from './pages/HomePage.vue';
  import CategoriaPage from './pages/CategoriaPage.vue';

  const pagina = ref(0);
  const paginas = [
    { label: 'Início', comp: HomePage },
    { label: 'Categorias', comp: CategoriaPage }
  ];

  // Dados globais
  const pontos = ref(pontosData);
  provide("pontos", pontos);
</script>

<template>
  <nav>
    <button v-for="(aba, idx) in paginas" :key="idx" @click="pagina = idx">
      {{ aba.label }}
    </button>
  </nav>
  <KeepAlive>
    <component :is="paginas[pagina].comp" />
  </KeepAlive>
</template>

<style scoped>
  nav {
    display: flex;
    gap: 10px;
    padding: 10px;
  }

  nav button {
    background: #4a90e2;
    color: white;
    border: none;
    padding: 10px 16px;
    border-radius: 6px;
    cursor: pointer;
    font-size: 15px;
    transition: 0.2s;
  }

  nav button:hover {
    background: #357ab8;
  }
</style>