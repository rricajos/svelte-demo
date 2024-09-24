<script>
	let cliente = 'manolo'; // Cambia por el cliente deseado
	let estadisticas = {};

	async function obtenerEstadisticas() {
			const response = await fetch(`http://localhost:3000/api/estadisticas/${cliente}`);
			if (response.ok) {
					estadisticas = await response.json();
			} else {
					console.error('Error al obtener estadísticas:', response.statusText);
			}
	}

	obtenerEstadisticas();
</script>

<main>
	<h1>Estadísticas de {cliente}</h1>
	{#if estadisticas.horarios}
			<h2>Horarios</h2>
			<ul>
					{#each Object.entries(estadisticas.horarios) as [dia, horario]}
							<li>{dia}: {horario.apertura} - {horario.cierre}</li>
					{/each}
			</ul>
	{/if}
</main>

<style>
	main {
			text-align: center;
			padding: 1em;
			max-width: 240px;
			margin: 0 auto;
	}
</style>
