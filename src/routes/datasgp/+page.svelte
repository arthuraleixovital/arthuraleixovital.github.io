<script>
	import { datasgp } from '$lib/datasgp.js'; // Importe o vetor de dados dos GPs
	import './stylesdatasgp.css';

	// Estado para armazenar o filtro e os dados filtrados
	let pesquisa = $state('');
	let filtrados = $state(datasgp);

	// Função para filtrar os GPs com base na pesquisa
	function filtrarGp() {
		if (pesquisa.trim() === '') {
			filtrados = datasgp; // Se a pesquisa estiver vazia, exibe todos os GPs
		} else {
			filtrados = datasgp.filter(
				(dgp) => dgp.nome.toLowerCase().includes(pesquisa.toLowerCase()) // Filtra pelo nome
			);
		}
	}
</script>

<div class="row align-items-center mb-3">
	<div class="col-md-4">
		<div class="input-group">
			<input
				class="form-control rounded-pill border-0 shadow-sm"
				type="text"
				placeholder="Pesquisar GPs..."
				bind:value={pesquisa}
				oninput={filtrarGp}
				aria-label="Pesquisar GPs"
				style="height: 40px;"
			/>
		</div>
	</div>
</div>

<!-- Cartões dos GPs filtrados -->
<div class="row row-cols-1 row-cols-md-3 g-4 mt-2">
	{#each filtrados as dgp}
		<div class="col">
			<div class="card shadow-lg rounded-3 h-100">
				<img
					src={dgp.img}
					class="card-img-top rounded-top"
					alt={dgp.nome}
					style="height: 300px; width: auto;"
				/>
				<div class="card-body">
					<h3>{dgp.nome}</h3>
					<p class="card-text text-muted">
						País: <b>{dgp.pais}&nbsp;</b>
						<img
							src={dgp.bandeira}
							style="height: 20px; width: auto; border: 1px solid #000;"
							alt="bandeiras"
						/>
					</p>
					<p class="card-text text-muted">Data: <b>{dgp.data}</b></p>
				</div>
			</div>
		</div>
	{/each}
</div>

<!-- Footer -->
<footer class="bg-dark text-white py-3 mt-4">
	<div class="container text-center">
		<p>&copy; 2025 GO F1 - Todos os direitos reservados.</p>
		<p>Contato: arthur.santos4@estudante.ifms.edu.br</p>
	</div>
</footer>