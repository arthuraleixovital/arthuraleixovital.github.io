<script>
    let { children } = $props();
</script>
 
<nav class="navbar navbar-expand-lg navbar-light bg-light">
    <div class="container-fluid d-flex justify-content-between">
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav mb-2 mb-lg-0 mx-auto"> <!-- mx-auto garante a centralização -->
          <li class="nav-item">
            <a class="nav-link" href="/">Inicial</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="/gp">Datas GPs</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="/equipes">Equipes</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
  
 
{@render children()}
