<script>
	import { onMount } from 'svelte';
	import { noticias } from '$lib/noticias.js';

	let gp = 'Austrália';

	// Defina a data do próximo Grand Prix
	const grandPrixDate = new Date('2025-03-14T04:00:00');

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
	<header class="bg-dark text-white py-3" style="height: 70px;">
		<div class="container text-center">
			<p class="lead">As últimas notícias do mundo da Fórmula 1</p>
		</div>
	</header>

	<!-- Notícias em destaque -->
	<section class="container mt-4">
		<h2 class="mb-4">Notícias em Destaque</h2>
		<div class="row">
			{#each noticias as noticiasd}
				<div class="col-md-4">
					<div
						class="card mb-3 h-100"
						style="height: 420px; display: flex; flex-direction: column; justify-content: space-between;"
					>
						<img
							src={noticiasd.imagem}
							class="card-img-top"
							alt={noticiasd.titulo}
							style="object-fit: cover; height: 200px;"
						/>
						<div class="card-body d-flex flex-column">
							<div>
								<h5 class="card-title"><b>{noticiasd.titulo}</b></h5>
								<p class="card-text">{noticiasd.resumo}</p>
							</div>
							<div class="mt-auto d-flex justify-content-between align-items-center">
								<a href={noticiasd.link} class="btn btn-dark">Leia mais</a>
								<span class="text-muted">{noticiasd.datan}</span>
							</div>
						</div>
					</div>
				</div>
			{/each}
		</div>
	</section>

	<hr />

	<div class="container text-center">
		<div class="timer">
			<p class="lead">O próximo Grand Prix será na <span class="fw-bold">{gp}.</span></p>
			<p>Restam apenas:</p>
			<p>
				<span class="fw-bold">{dias}</span> dias,
				<span class="fw-bold">{horas}</span> horas,
				<span class="fw-bold">{minutos}</span> minutos e
				<span class="fw-bold">{segundos}</span> segundos
			</p>
		</div>
		<img
			src="aust.jpg"
			class="card-img-top mt-4"
			style="height: 400px; object-fit: cover; border-radius: 12px;"
			alt="GP da Australia."
		/>
	</div>

	<!-- Footer -->
	<footer class="bg-dark text-white py-3 mt-4">
		<div class="container text-center">
			<p>&copy; 2025 GO F1 - Todos os direitos reservados.</p>
			<p>Contato: arthur.santos4@estudante.ifms.edu.br</p>
		</div>
	</footer>
</main>

<style>
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
	.card {
		transition:
			transform 0.3s ease,
			box-shadow 0.3s ease; /* Suaviza as transformações */
	}

	.card:hover {
		transform: translateY(-10px); /* Eleva o card ao passar o mouse */
		box-shadow: 0 10px 20px rgba(0, 0, 0, 0.7); /* Adiciona uma sombra maior */
		transform: scale(1.05); /* Aumenta ligeiramente a imagem no hover */
	}

	.card img {
		transition: transform 0.3s ease; /* Suaviza o zoom na imagem */
	}
	/* Estilo para o container da data e botão */
	.card .card-body .mt-auto {
		display: flex;
		justify-content: space-between; /* Distribui espaço entre a data e o botão */
		align-items: center; /* Alinha verticalmente ao centro */
	}

	/* Container flex para botão e data */
	.card .card-body .mt-auto {
		display: flex;
		justify-content: space-between; /* Espaço entre os itens */
		align-items: center; /* Alinhamento vertical */
	}

	/* Estilo do botão (à esquerda) */
	.card .card-body .btn {
		margin-right: auto; /* Mantém o botão no lado esquerdo */
	}

	/* Estilo da data (à direita) */
	.card .card-body .text-muted {
		font-size: 0.85rem; /* Tamanho da fonte da data */
		color: #6c757d; /* Cor cinza discreta */
		margin-left: auto; /* Empurra a data para o lado direito */
	}
</style>