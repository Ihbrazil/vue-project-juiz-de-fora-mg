<script setup>
    import { inject, ref, computed } from 'vue';
    import CardPonto from '../components/CardPonto.vue';
    const pontos = inject("pontos")
    const categoriaSelecionada = ref("Parques")

    const categorias = computed(() => [...new Set(pontos.value.map(p => p.categoria))])
    const filtrados = computed(() => pontos.value.filter(p => p.categoria === categoriaSelecionada.value))
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
h1 {
  font-size: 26px;
  margin: 20px 0 10px;
  text-align: center;
  color: #333;
}

/* Estilo do select */
select {
  display: block;
  margin: 0 auto 20px;
  padding: 10px 14px;
  font-size: 16px;
  border-radius: 6px;
  border: 1px solid #ccc;
  background: #fff;
  cursor: pointer;
  transition: border-color 0.2s;
}

select:hover {
  border-color: #4a90e2;
}

/* Galeria de cards */
.galeria {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
  gap: 20px;
  padding: 20px;
}
</style>