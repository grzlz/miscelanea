<script>
	let { products = $bindable([]), onProductClick = () => {} } = $props();
	
	const sampleProducts = [
		{
			id: 1,
			name: "Tequila Don Julio 1942",
			price: "$2,450",
			image: "/don-julio.jpg",
			category: "Tequila",
			description: "Tequila añejo premium"
		},
		{
			id: 2,
			name: "Whisky Macallan 18",
			price: "$8,500",
			image: "/macallan.jpg",
			category: "Whisky",
			description: "Whisky escocés single malt"
		},
		{
			id: 3,
			name: "Ron Zacapa 23",
			price: "$1,200",
			image: "/zacapa.jpg",
			category: "Ron",
			description: "Ron guatemalteco premium"
		},
		{
			id: 4,
			name: "Vodka Grey Goose",
			price: "$850",
			image: "/grey-goose.webp",
			category: "Vodka",
			description: "Vodka francés premium"
		},
		{
			id: 5,
			name: "Cognac Hennessy XO",
			price: "$3,200",
			image: "/hennessy.jpg",
			category: "Cognac",
			description: "Cognac francés extra old"
		},
		{
			id: 6,
			name: "Mezcal 400 Conejos",
			price: "$950",
			image: "/conejos.jpg",
			category: "Mezcal",
			description: "Mezcal artesanal oaxaqueño"
		}
	];
	
	let displayProducts = $derived(products.length > 0 ? products : sampleProducts);
</script>

<section class="py-12 px-4">
	<div class="max-w-7xl mx-auto">
		<h2 class="text-3xl md:text-4xl font-bold text-center mb-12 bg-gradient-to-r from-amber-600 to-orange-600 bg-clip-text text-transparent">
			Lo más vendido
		</h2>
		{#if displayProducts.length === 0}
			<div class="text-center py-20">
				<p class="text-gray-500 text-xl">No se encontraron productos</p>
			</div>
		{:else}
			<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-8">
				{#each displayProducts as product, i}
					<div 
						class="group bg-white rounded-2xl shadow-lg hover:shadow-2xl transition-all duration-500 cursor-pointer border border-gray-100 overflow-hidden transform hover:-translate-y-2 hover:rotate-1"
						on:click={() => onProductClick(product)}
						on:keypress={(e) => e.key === 'Enter' && onProductClick(product)}
						tabindex="0"
						role="button"
						style="animation-delay: {i * 100}ms"
					>
						<div class="relative w-full h-80 bg-gradient-to-br from-gray-100 to-gray-200 overflow-hidden">
							<img 
								src={product.image} 
								alt={product.name}
								class="w-full h-full object-contain transition-all duration-500 group-hover:scale-110"
							>
							<div class="absolute inset-0 bg-gradient-to-t from-black/20 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
							<div class="absolute top-3 right-3 opacity-0 group-hover:opacity-100 transition-all duration-300 transform translate-y-2 group-hover:translate-y-0">
								<div class="bg-white/90 backdrop-blur-sm rounded-full p-2 shadow-lg">
									<svg class="w-5 h-5 text-amber-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
										<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6v6m0 0v6m0-6h6m-6 0H6"></path>
									</svg>
								</div>
							</div>
						</div>
						<div class="p-6">
							<div class="flex justify-between items-start mb-2">
								<h3 class="font-bold text-lg text-gray-900 group-hover:text-amber-600 transition-colors duration-300">{product.name}</h3>
							</div>
							<p class="text-gray-600 text-sm mb-4 line-clamp-2">{product.description}</p>
							<div class="flex justify-between items-center">
								<p class="text-2xl font-bold bg-gradient-to-r from-amber-600 to-orange-600 bg-clip-text text-transparent">{product.price}</p>
								<span class="px-3 py-1 bg-gradient-to-r from-amber-100 to-orange-100 text-amber-800 text-xs font-semibold rounded-full border border-amber-200">
									{product.category}
								</span>
							</div>
							<div class="mt-4 opacity-0 group-hover:opacity-100 transition-all duration-300 transform translate-y-2 group-hover:translate-y-0">
								<div class="w-full h-1 bg-gradient-to-r from-amber-600 to-orange-600 rounded-full"></div>
							</div>
						</div>
					</div>
				{/each}
			</div>
		{/if}
	</div>
</section>