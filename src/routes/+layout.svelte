<script>
	import './styleslayout.css';
</script>

<body>
	<img src="logo.png" alt="Logo" class="top-left-image" />

	<nav class="navbar navbar-expand navbar-light">
		<div class="container-fluid d-flex justify-content-between">
			<div class="collapse navbar-collapse" id="navbarSupportedContent">
				<ul class="navbar-nav mb-2 mb-lg-0 mx-auto">
					<li class="nav-item">
						<a class="nav-link" href="/"><b>Inicial</b></a>
					</li>
					<li class="nav-item">
						<a class="nav-link" href="/datasgp"><b>Datas GPs</b></a>
					</li>
					<li class="nav-item">
						<a class="nav-link" href="/equipes"><b>Equipes</b></a>
					</li>
				</ul>
			</div>
		</div>
	</nav>
</body>
<slot />
