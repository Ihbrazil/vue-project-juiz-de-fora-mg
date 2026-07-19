<script setup>
  defineProps({ ponto: Object });
</script>

<template>
  <div class="card">
    <img :src="ponto.img" :alt="ponto.nome" />
    <h2>{{ ponto.nome }}</h2>
    <p>{{ ponto.descricao }}</p>
    <span class="categoria">{{ ponto.categoria }}</span>
  </div>
</template>

<style scoped>
.card {
  background: white;
  border-radius: 10px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  padding: 15px;
  text-align: center;
  transition: transform 0.2s;
}

.card:hover {
  transform: translateY(-4px);
}

.card img {
  width: 100%;
  height: 150px;
  object-fit: cover;
  border-radius: 8px;
}

.card h2 {
  margin: 10px 0 5px;
  font-size: 18px;
}

.card p {
  font-size: 14px;
  color: #555;
}

.categoria {
  display: inline-block;
  margin-top: 8px;
  padding: 4px 8px;
  background: #eee;
  border-radius: 6px;
  font-size: 12px;
  color: #333;
}
</style>