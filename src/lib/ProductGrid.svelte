<script>
	let { products = $bindable([]), onProductClick = () => {} } = $props();
	
	const sampleProducts = [
		{
			id: 1,
			name: "Tequila Don Julio 1942",
			price: "$2,450",
			image: "https://via.placeholder.com/300x400/amber/white?text=Tequila",
			category: "Tequila",
			description: "Tequila añejo premium"
		},
		{
			id: 2,
			name: "Whisky Macallan 18",
			price: "$8,500",
			image: "https://via.placeholder.com/300x400/amber/white?text=Whisky",
			category: "Whisky",
			description: "Whisky escocés single malt"
		},
		{
			id: 3,
			name: "Ron Zacapa 23",
			price: "$1,200",
			image: "https://via.placeholder.com/300x400/amber/white?text=Ron",
			category: "Ron",
			description: "Ron guatemalteco premium"
		},
		{
			id: 4,
			name: "Vodka Grey Goose",
			price: "$850",
			image: "https://via.placeholder.com/300x400/amber/white?text=Vodka",
			category: "Vodka",
			description: "Vodka francés premium"
		},
		{
			id: 5,
			name: "Cognac Hennessy XO",
			price: "$3,200",
			image: "https://via.placeholder.com/300x400/amber/white?text=Cognac",
			category: "Cognac",
			description: "Cognac francés extra old"
		},
		{
			id: 6,
			name: "Mezcal Del Maguey",
			price: "$950",
			image: "https://via.placeholder.com/300x400/amber/white?text=Mezcal",
			category: "Mezcal",
			description: "Mezcal artesanal oaxaqueño"
		}
	];
	
	let displayProducts = $derived(products.length > 0 ? products : sampleProducts);
</script>

<section class="py-12 px-4">
	<div class="max-w-7xl mx-auto">
		{#if displayProducts.length === 0}
			<div class="text-center py-20">
				<p class="text-gray-500 text-xl">No se encontraron productos</p>
			</div>
		{:else}
			<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-6">
				{#each displayProducts as product}
					<div 
						class="bg-white rounded-lg shadow-md hover:shadow-lg transition-shadow cursor-pointer border border-gray-200"
						on:click={() => onProductClick(product)}
						on:keypress={(e) => e.key === 'Enter' && onProductClick(product)}
						tabindex="0"
						role="button"
					>
						<div class="aspect-[3/4] bg-gray-100 rounded-t-lg overflow-hidden">
							<img 
								src={product.image} 
								alt={product.name}
								class="w-full h-full object-cover"
							>
						</div>
						<div class="p-4">
							<h3 class="font-semibold text-lg text-gray-900 mb-1">{product.name}</h3>
							<p class="text-gray-600 text-sm mb-2">{product.description}</p>
							<p class="text-2xl font-bold text-amber-600">{product.price}</p>
							<span class="inline-block mt-2 px-2 py-1 bg-amber-100 text-amber-800 text-xs rounded-full">
								{product.category}
							</span>
						</div>
					</div>
				{/each}
			</div>
		{/if}
	</div>
</section>