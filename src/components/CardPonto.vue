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
  /* Card base */
  .card {
    background: #fff;
    border-radius: 14px;
    box-shadow: 0 4px 14px rgba(0,0,0,0.08);
    padding: 18px;
    text-align: center;
    transition: transform 0.25s ease, box-shadow 0.25s ease;
    overflow: hidden;
  }

  /* Hover elegante */
  .card:hover {
    transform: translateY(-6px);
    box-shadow: 0 8px 20px rgba(0,0,0,0.12);
  }

  /* Imagem */
  .card img {
    width: 100%;
    height: 170px;
    object-fit: cover;
    border-radius: 10px;
    transition: transform 0.3s ease;
  }

  /* Zoom suave na imagem */
  .card:hover img {
    transform: scale(1.03);
  }

  /* Título */
  .card h2 {
    margin: 12px 0 6px;
    font-size: 20px;
    font-weight: 600;
    color: #444;
  }

  /* Descrição */
  .card p {
    font-size: 15px;
    color: #666;
    line-height: 1.4;
    margin-bottom: 10px;
  }

  /* Categoria */
  .categoria {
    display: inline-block;
    margin-top: 10px;
    padding: 6px 10px;
    background: #f2f2f2;
    border-radius: 8px;
    font-size: 13px;
    color: #555;
    font-weight: 500;
  }

  /* Tablets */
  @media (max-width: 1024px) {
    .card img {
      height: 150px;
    }
  }

  /* Celulares grandes */
  @media (max-width: 768px) {
    .card {
      padding: 14px;
    }

    .card img {
      height: 140px;
    }

    .card h2 {
      font-size: 18px;
    }

    .card p {
      font-size: 14px;
    }
  }

  /* Celulares pequenos */
  @media (max-width: 480px) {
    .card {
      padding: 12px;
    }

    .card img {
      height: 130px;
    }

    .card h2 {
      font-size: 17px;
    }

    .card p {
      font-size: 13px;
    }

    .categoria {
      font-size: 12px;
      padding: 4px 8px;
    }
  }

  /* Notebooks grandes */
  @media (min-width: 1280px) {
    .card {
      padding: 22px;
    }

    .card img {
      height: 190px;
    }

    .card h2 {
      font-size: 22px;
    }

    .card p {
      font-size: 16px;
    }
  }
</style>