<script>
    import { equipes } from '$lib/equipes.js';
</script>

<style>
    .card {
      transition: transform 0.3s ease, box-shadow 0.3s ease; /* Suaviza as transformações */
      border-radius: 1rem; /* Adiciona bordas arredondadas ao card */
    }
    
    .card-img-top {
      object-fit: cover;
      height: 200px; /* Ajuste a altura das imagens */
      transition: transform 0.3s ease; /* Efeito de zoom ao passar o mouse */
      border-top-left-radius: 1rem; /* Mantém as bordas arredondadas da imagem */
      border-top-right-radius: 1rem;
    }
    
    .card:hover {
      transform: translateY(-10px); /* Eleva o card ao passar o mouse */
      box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); /* Sombra mais suave e visível */
      transform: scale(1.05); /* Aumenta ligeiramente o card no hover */
    }
    
    .card-body {
      background-color: #f8f9fa; /* Cor de fundo clara */
      border-bottom-left-radius: 1rem; /* Mantém as bordas arredondadas no corpo do card */
      border-bottom-right-radius: 1rem;
    }
</style>
    
<!-- Adicionando uma margem superior para afastar os cards da navbar -->
<div class="row row-cols-1 row-cols-md-3 g-4 mt-2"> <!-- mt-5 adiciona uma margem superior -->
  {#each equipes as equipe}
  <div class="col">
    <div class="card shadow-lg rounded-3 h-100">
      <img src={equipe.img} class="card-img-top rounded-top" alt="{equipe.nome}">
      <div class="card-body">
        <h3>{equipe.nome}</h3>
        <p class="card-text text-muted">Pilotos: <b>{equipe.pilotos}</b></p>
        <p class="card-text text-muted">Engenheiro: <b>{equipe.engenheiro}</b></p>
        <p class="card-text text-muted">Campeonatos de construtores vencidos: <b>{equipe.campcons}</b></p>
      </div>
    </div>
  </div>
  {/each}
</div>
