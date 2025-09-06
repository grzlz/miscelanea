<script>
	import { page } from '$app/stores';
	import UnderConstruction from '$lib/UnderConstruction.svelte';
	
	let status = $derived($page.error?.status || 404);
	let message = $derived($page.error?.message || 'Página no encontrada');
</script>

<svelte:head>
	<title>{status} - {message} | La Miscelánea</title>
</svelte:head>

{#if status === 404}
	<UnderConstruction 
		pageTitle="Esta página" 
		message="Estamos trabajando en el sitio" 
	/>
{:else}
	<UnderConstruction 
		pageTitle="Esta sección" 
		message="Algo salió mal" 
	/>
{/if}