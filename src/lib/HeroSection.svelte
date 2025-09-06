<script>
	let { onSearch = () => {} } = $props();
	
	let searchTerm = $state('');
	
	function handleSearch() {
		onSearch(searchTerm);
	}
	
	function handleKeyPress(event) {
		if (event.key === 'Enter') {
			handleSearch();
		}
	}
</script>

<section class="bg-gradient-to-br from-amber-50 to-orange-100 py-20 px-4">
	<div class="max-w-4xl mx-auto text-center">
		<h1 class="text-5xl font-bold text-gray-900 mb-4">La Miscelánea</h1>
		<h2 class="text-3xl font-semibold text-gray-800 mb-8">Haz tu pedido</h2>
		
		<div class="max-w-2xl mx-auto">
			<div class="flex gap-2">
				<input 
					bind:value={searchTerm}
					on:keypress={handleKeyPress}
					type="text" 
					placeholder="Buscar productos..." 
					class="flex-1 px-6 py-4 text-lg border border-gray-300 rounded-l-lg focus:outline-none focus:ring-2 focus:ring-amber-500 focus:border-transparent"
				>
				<button 
					on:click={handleSearch}
					class="px-8 py-4 bg-amber-600 text-white font-semibold rounded-r-lg hover:bg-amber-700 transition-colors"
				>
					Buscar
				</button>
			</div>
		</div>
	</div>
</section>