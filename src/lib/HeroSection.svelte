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

<section class="relative bg-gradient-to-br from-amber-50 via-orange-50 to-amber-100 py-24 px-4 overflow-hidden">
	<!-- Animated background elements -->
	<div class="absolute inset-0 opacity-10">
		<div class="absolute top-10 left-10 w-32 h-32 bg-amber-400 rounded-full blur-3xl animate-pulse"></div>
		<div class="absolute bottom-10 right-10 w-48 h-48 bg-orange-400 rounded-full blur-3xl animate-pulse delay-1000"></div>
		<div class="absolute top-1/2 left-1/2 w-24 h-24 bg-yellow-400 rounded-full blur-2xl animate-bounce delay-500"></div>
	</div>
	
	<div class="max-w-4xl mx-auto text-center relative z-10">
		<h1 class="text-5xl md:text-6xl font-bold text-gray-900 mb-4 animate-fade-in-up">
			Haz tu <span class="bg-gradient-to-r from-amber-600 to-orange-600 bg-clip-text text-transparent">pedido</span>
		</h1>
		<p class="text-xl text-gray-600 mb-12 animate-fade-in-up delay-200">
			Encuentra los mejores productos para tu negocio
		</p>
		
		<div class="max-w-2xl mx-auto animate-fade-in-up delay-400">
			<div class="relative group">
				<div class="absolute -inset-0.5 bg-gradient-to-r from-amber-600 to-orange-600 rounded-2xl blur opacity-30 group-hover:opacity-50 transition duration-300"></div>
				<div class="relative flex bg-white rounded-2xl shadow-xl">
					<input 
						bind:value={searchTerm}
						on:keypress={handleKeyPress}
						type="text" 
						placeholder="Buscar productos..." 
						class="flex-1 px-8 py-5 text-lg bg-transparent border-none rounded-l-2xl focus:outline-none focus:ring-0 placeholder-gray-400"
					>
					<button 
						on:click={handleSearch}
						class="px-10 py-5 bg-gradient-to-r from-amber-600 to-orange-600 text-white font-semibold rounded-r-2xl hover:from-amber-700 hover:to-orange-700 transition-all duration-300 transform hover:scale-105 active:scale-95 shadow-lg hover:shadow-xl"
					>
						<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path>
						</svg>
					</button>
				</div>
			</div>
		</div>
	</div>
</section>

<style>
	@keyframes fade-in-up {
		from {
			opacity: 0;
			transform: translateY(30px);
		}
		to {
			opacity: 1;
			transform: translateY(0);
		}
	}
	
	.animate-fade-in-up {
		animation: fade-in-up 0.8s ease-out forwards;
	}
	
	.delay-200 {
		animation-delay: 0.2s;
		opacity: 0;
	}
	
	.delay-400 {
		animation-delay: 0.4s;
		opacity: 0;
	}
</style>