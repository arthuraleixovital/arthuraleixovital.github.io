<script>
  import { onMount } from "svelte";

  let noticiasDestaque = [
    { id: 1, titulo: "Lewis Hamilton na Ferrari", resumo: "Lewis Hamilton, 7 vezes campeão assina contrato com a Escuderia Ferrari.", imagem: "lw.jpg", link: "https://ge.globo.com/motor/formula-1/noticia/2024/02/01/mercedes-confirma-saida-de-lewis-hamilton-ao-fim-da-f1-2024.ghtml" },
    { id: 2, titulo: "Gabriel Bortoleto na Kick Sauber", resumo: "Gabriel Bortoleto, brasileiro, campeão da F3 e F2, assina um contrato multi-anual com a Kick Sauber. ", imagem: "gb.png", link: "https://www.band.uol.com.br/esportes/automobilismo/formula-1/noticias/anuncio-gabriel-bortoleto-f1-202408272058" },
    { id: 3, titulo: "Liam Lawson assina com Redbull Racing", resumo: "Liam Lawson, ex corredor da Visa Cash App RB, assina contrato com a Redbull Racing, substituindo o piloto Sergio Perez.", imagem: "liam.png", link: "https://ge.globo.com/motor/formula-1/noticia/2024/12/19/rbr-anuncia-liam-lawson-no-lugar-de-sergio-perez-na-f1-2025.ghtml" },
  ];

  let gp = "Austrália"


// Defina a data do próximo Grand Prix
const grandPrixDate = new Date("2025-03-14T04:00:00");

// Variáveis para exibir o tempo restante
let dias = 0;
let horas = 0;
let minutos = 0;
let segundos = 0;

// Função para calcular o tempo restante
function calcularTempoRestante() {
  const agora = new Date();
  const diferenca = grandPrixDate - agora;

  if (diferenca > 0) {
    dias = Math.floor(diferenca / (1000 * 60 * 60 * 24));
    horas = Math.floor((diferenca % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
    minutos = Math.floor((diferenca % (1000 * 60 * 60)) / (1000 * 60));
    segundos = Math.floor((diferenca % (1000 * 60)) / 1000);
  } else {
    dias = horas = minutos = segundos = 0; // Timer zerado
  }
}

// Atualize o contador a cada segundo
onMount(() => {
  const interval = setInterval(() => {
    calcularTempoRestante();
  }, 1000);

  return () => clearInterval(interval); // Limpa o intervalo quando o componente é destruído
});
</script>


<main>
  <!-- Header -->
  <header class="bg-dark text-white py-3">
    <div class="container text-center">
      <img src="logo.png" style="width: 200px;">
      <p class="lead">As últimas notícias do mundo da Fórmula 1</p>
    </div>
  </header>

  <!-- Notícias em destaque -->
  <section class="container mt-4">
    <h2 class="mb-4">Notícias em Destaque</h2>
    <div class="row">
      {#each noticiasDestaque as noticia}
        <div class="col-md-4">
          <div class="card mb-3 h-100" style="height: 420px; display: flex; flex-direction: column; justify-content: space-between;">
            <img src={noticia.imagem} class="card-img-top" alt={noticia.titulo} style="object-fit: cover; height: 200px;">
            <div class="card-body d-flex flex-column">
              <div>
                <h5 class="card-title"><b>{noticia.titulo}</b></h5>
                <p class="card-text">{noticia.resumo}</p>
              </div>
              <div class="mt-auto">
                <a href={noticia.link} class="btn btn-primary">Leia mais</a>
              </div>
            </div>
          </div>
        </div>
      {/each}
    </div>
  </section>

<hr>

    <div class="container text-center">
      <div class="timer">
        <p class="lead">O próximo Grand Prix será na <span class="fw-bold">{gp}</span>.</p>
        <p>Restam apenas:</p>
        <p>
          <span class="fw-bold">{dias}</span> dias, 
          <span class="fw-bold">{horas}</span> horas, 
          <span class="fw-bold">{minutos}</span> minutos e 
          <span class="fw-bold">{segundos}</span> segundos
        </p>
      </div>
      <img src="aust.jpg" class="card-img-top mt-4" style="height: 400px; object-fit: cover; border-radius: 12px;">
    </div>

  <!-- Footer -->
  <footer class="bg-dark text-white py-3 mt-4">
    <div class="container text-center">
      <p>&copy; 2025 GO F1 - Todos os direitos reservados.</p>
    </div>
  </footer>
</main>

<style>
  h1, h2 {
    font-family: Arial, sans-serif;
  }

  .card-img-top {
    height: 200px;
    object-fit: cover;
  }

  .timer {
    font-family: Arial, sans-serif;
    font-size: 1.5rem;
    text-align: center;
    padding: 1rem;
    background-color: #f8f9fa;
    border-radius: 8px;
    box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
    display: inline-block;
    margin: auto;
  }

  .timer span {
    font-weight: bold;
    color: #dc3545;
    margin: 0 4px;
  }
</style>


