<script>
	let mobileMenuOpen = $state(false);
	
	function toggleMobileMenu() {
		mobileMenuOpen = !mobileMenuOpen;
	}
</script>

<nav class="bg-white/95 backdrop-blur-sm shadow-lg border-b border-amber-100 sticky top-0 z-40 transition-all duration-300">
	<div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
		<div class="flex justify-between items-center h-16">
			<!-- Logo -->
			<div class="flex items-center group">
				<img 
					src="/logo.png" 
					alt="La Miscelánea" 
					class="h-10 w-auto transition-transform duration-300 group-hover:scale-110"
				>
			</div>
			
			<!-- Desktop Navigation -->
			<div class="hidden md:block">
				<div class="flex items-center space-x-8">
					<a href="/" class="text-gray-700 hover:text-amber-600 font-medium transition-all duration-300 relative group">
						Inicio
						<span class="absolute -bottom-1 left-0 w-0 h-0.5 bg-amber-600 transition-all duration-300 group-hover:w-full"></span>
					</a>
					<a href="/productos" class="text-gray-700 hover:text-amber-600 font-medium transition-all duration-300 relative group">
						Productos
						<span class="absolute -bottom-1 left-0 w-0 h-0.5 bg-amber-600 transition-all duration-300 group-hover:w-full"></span>
					</a>
					<a href="/pedidos" class="text-gray-700 hover:text-amber-600 font-medium transition-all duration-300 relative group">
						Mis Pedidos
						<span class="absolute -bottom-1 left-0 w-0 h-0.5 bg-amber-600 transition-all duration-300 group-hover:w-full"></span>
					</a>
					<a href="/contacto" class="text-gray-700 hover:text-amber-600 font-medium transition-all duration-300 relative group">
						Contacto
						<span class="absolute -bottom-1 left-0 w-0 h-0.5 bg-amber-600 transition-all duration-300 group-hover:w-full"></span>
					</a>
					<button class="bg-gradient-to-r from-amber-600 to-amber-700 text-white px-6 py-2 rounded-full font-medium hover:from-amber-700 hover:to-amber-800 transition-all duration-300 transform hover:scale-105 shadow-lg hover:shadow-xl">
						Hacer Pedido
					</button>
				</div>
			</div>
			
			<!-- Mobile menu button -->
			<div class="md:hidden">
				<button 
					on:click={toggleMobileMenu}
					class="text-gray-700 hover:text-amber-600 p-2"
					aria-label="Abrir menú"
				>
					<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" 
							d={mobileMenuOpen ? "M6 18L18 6M6 6l12 12" : "M4 6h16M4 12h16M4 18h16"}></path>
					</svg>
				</button>
			</div>
		</div>
	</div>
	
	<!-- Mobile Navigation -->
	{#if mobileMenuOpen}
		<div class="md:hidden bg-white border-t border-gray-200">
			<div class="px-4 py-3 space-y-3">
				<a href="/" class="block text-gray-700 hover:text-amber-600 font-medium py-2 transition-colors">
					Inicio
				</a>
				<a href="/productos" class="block text-gray-700 hover:text-amber-600 font-medium py-2 transition-colors">
					Productos
				</a>
				<a href="/pedidos" class="block text-gray-700 hover:text-amber-600 font-medium py-2 transition-colors">
					Mis Pedidos
				</a>
				<a href="/contacto" class="block text-gray-700 hover:text-amber-600 font-medium py-2 transition-colors">
					Contacto
				</a>
				<button class="w-full bg-amber-600 text-white px-4 py-2 rounded-md font-medium hover:bg-amber-700 transition-colors">
					Hacer Pedido
				</button>
			</div>
		</div>
	{/if}
</nav>