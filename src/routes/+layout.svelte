<script>
  let { children } = $props();
</script>

<style>
  /* Adiciona o gradiente animado apenas para a barra de navegação */
  .navbar {
      background: linear-gradient(45deg, #8d0e02, #440202, #8d0e02);
      background-size: 400% 100%;  /* Expande o gradiente para criar o movimento */
      animation: gradientAnimation 15s ease-in-out infinite;  /* Animação de ida e volta */
      position: relative; /* Define posição relativa para referência */
      z-index: 1; /* Garante que a barra de navegação fique abaixo da imagem */
  }
  @keyframes gradientAnimation {
      0% {
          background-position: 0% 50%;  /* Gradiente começa à esquerda */
      }
      50% {
          background-position: 100% 50%;  /* Gradiente move-se para a direita */
      }
      100% {
          background-position: 0% 50%;  /* Gradiente volta para a posição inicial */
      }
  }

  /* Estilo para a barra de navegação */
  .navbar-light {
      background-color: rgba(255, 255, 255, 0.8); /* Transparente para mostrar o gradiente */
  }
  .navbar-light .navbar-nav .nav-link {
      color: #ffffff; /* Cor do texto */
  }
  /* Remove padding e margens padrão do body para evitar problemas */
  body {
      margin: 0;
      padding: 0;
  }

  /* Posiciona a imagem exatamente em cima da navbar */
  .top-left-image {
      position: absolute; /* Fixa a imagem */
      top: -20px; /* Posiciona no topo da página */
      left: 0; /* Alinha ao canto esquerdo */
      z-index: 9999; /* Garante que a imagem fique acima da barra de navegação */
      width: 100px; /* Define a largura da imagem */
      height: auto; /* Mantém a proporção da imagem */
  }

  /* Ajusta a altura da navbar para evitar sobreposição com a imagem */
  .navbar {
      padding-top: 10px; /* Dá espaço suficiente abaixo da imagem */
  }
  body {
  overflow-x: hidden; /* Impede a rolagem horizontal */
  margin: 0; /* Remove margens extras */
  padding: 0; /* Remove padding extra */
  }
.row {
  overflow-x: hidden; /* Impede a rolagem dentro da linha */
  }
</style>

<body>
  <!-- Adiciona a imagem no canto superior esquerdo -->
  <img src="logo.png" alt="Logo" class="top-left-image">

  <nav class="navbar navbar-expand-lg navbar-light">
    <div class="container-fluid d-flex justify-content-between">
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav mb-2 mb-lg-0 mx-auto"> <!-- mx-auto garante a centralização -->
          <li class="nav-item">
            <a class="nav-link" href="/"><b>Inicial</b></a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="/gp"><b>Datas GPs</b></a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="/equipes"><b>Equipes</b></a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</body>

<footer class="bg-dark text-white py-3 mt-4">
  <div class="container text-center">
    <p>&copy; 2025 GO F1 - Todos os direitos reservados.</p>
  </div>
</footer>
<slot />
