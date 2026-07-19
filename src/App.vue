<script setup>
  import { ref, provide } from 'vue'
  import HomePage from './pages/HomePage.vue'
  import CategoriaPage from './pages/CategoriaPage.vue'

  const pagina = ref(0)
  const paginas = [
    { label: 'Início', comp: HomePage },
    { label: 'Categorias', comp: CategoriaPage }
  ]

  // Dados globais
  const pontos = ref([
    { id: 1, nome: "Parque Halfeld", categoria: "Parques", descricao: "Principal praça da cidade", img: "/parque.jpg" },

    { id: 2, nome: "Museu Mariano Procópio", categoria: "Museus", descricao: "Museu histórico e cultural", img: "/museu.jpg" },

    { id: 3, nome: "Mirante Morro do Cristo", categoria: "Mirantes", descricao: "Vista panorâmica da cidade", img: "/cristo.jpg" },

    { id: 4, nome: "Parque da Lajinha", categoria: "Parques", descricao: "Área verde com lago, trilhas e espaço para lazer", img: "/lajinha.jpg" },

    { id: 5, nome: "Catedral Metropolitana", categoria: "Igrejas", descricao: "Arquitetura neogótica e um dos cartões-postais da cidade", img: "/catedral.jpg" },

    { id: 6, nome: "Morro do Imperador", categoria: "Mirantes", descricao: "Mirante com vista ampla da cidade e área para caminhadas", img: "/imperador.jpg" },

    { id: 7, nome: "Centro Cultural Bernardo Mascarenhas", categoria: "Cultura", descricao: "Espaço cultural com exposições e eventos", img: "/ccbmascarenhas.jpg" },

    { id: 8, nome: "Planetário da UFJF", categoria: "Ciência", descricao: "Sessões educativas sobre astronomia e espaço", img: "/planetario.jpg" },

    { id: 9, nome: "Parque da Cidade", categoria: "Parques", descricao: "Parque amplo com quadras, pistas e áreas de convivência", img: "/parque_cidade.jpg" },

    { id: 10, nome: "Museu de Arte Murilo Mendes", categoria: "Museus", descricao: "Acervo moderno e exposições culturais variadas", img: "/mam.jpg" },

    { id: 11, nome: "Estádio Municipal", categoria: "Esportes", descricao: "Palco de jogos e eventos esportivos da cidade", img: "/estadio.jpg" },

    { id: 12, nome: "Shopping Independência", categoria: "Compras", descricao: "Centro comercial com lojas, cinema e alimentação", img: "/independencia.jpg" },

    { id: 13, nome: "Shopping Jardim Norte", categoria: "Compras", descricao: "Centro comercial moderno com lojas, cinema, restaurantes e eventos culturais", img: "/jardim_norte.jpg" },

    { id: 14, nome: "Mirante da BR-040", categoria: "Mirantes", descricao: "Mirante com vista ampla da cidade e da região, muito visitado ao pôr do sol", img: "/mirante_br040.jpg" },

    { id: 15, nome: "Paróquia Nossa Senhora da Glória", categoria: "Igrejas", descricao: "Igreja histórica situada no alto do Morro da Glória, com vista privilegiada da cidade", img: "/igreja_da_gloria.jpg"}
  ]);

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