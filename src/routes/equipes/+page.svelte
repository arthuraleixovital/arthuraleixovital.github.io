<script>
	import { equipes } from '$lib/equipes.js';
	import './stylesequipes.css';
</script>

<div class="row row-cols-1 row-cols-md-3 g-4 mt-2">
	{#each equipes as equipe}
		<div class="col">
			<div class="card shadow-lg rounded-3 h-100">
				<img src={equipe.img} class="card-img-top rounded-top" alt={equipe.nome} />
				<div class="card-body">
					<h3>{equipe.nome}</h3>
					<p class="card-text text-muted">Pilotos: <b>{equipe.pilotos}</b></p>
					<p class="card-text text-muted">Engenheiro: <b>{equipe.engenheiro}</b></p>
					<p class="card-text text-muted">
						Campeonatos de construtores vencidos: <b>{equipe.campcons}</b>
					</p>
				</div>
			</div>
		</div>
	{/each}
</div>

<footer class="bg-dark text-white py-3 mt-4">
	<div class="container text-center">
		<p>&copy; 2025 GO F1 - Todos os direitos reservados.</p>
		<p>Contato: arthur.santos4@estudante.ifms.edu.br</p>
	</div>
</footer>
