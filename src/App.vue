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
    gap: 12px;
    padding: 12px;
    justify-content: center;
    max-width: 1100px;     /* limite elegante */
    margin: 0 auto;        /* centraliza em telas grandes */
  }

  nav button {
    background: #4a90e2;
    color: white;
    border: none;
    padding: 10px 18px;
    border-radius: 6px;
    cursor: pointer;
    font-size: 15px;
    transition: 0.2s;
  }

  nav button:hover {
    background: #357ab8;
  }

  /* Tablets */
  @media (max-width: 1024px) {
    nav {
      max-width: 90%;
    }
  }

  /* Celulares grandes */
  @media (max-width: 768px) {
    nav {
      flex-wrap: wrap;
      gap: 10px;
    }

    nav button {
      width: 100%;
      text-align: center;
      padding: 12px;
      font-size: 16px;
    }
  }

  /* Celulares pequenos */
  @media (max-width: 480px) {
    nav {
      flex-direction: column;
      gap: 8px;
    }

    nav button {
      font-size: 15px;
    }
  }

  /* Notebooks grandes */
  @media (min-width: 1280px) {
    nav {
      max-width: 1200px;   /* limite maior, mas ainda elegante */
      gap: 16px;
    }

    nav button {
      padding: 12px 20px;
      font-size: 17px;
    }
  }
</style>