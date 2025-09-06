<script>
	import Navbar from '$lib/Navbar.svelte';
	import HeroSection from '$lib/HeroSection.svelte';
	import ProductGrid from '$lib/ProductGrid.svelte';
	import OrderModal from '$lib/OrderModal.svelte';
	
	let products = $state([]);
	let filteredProducts = $state([]);
	let selectedProduct = $state(null);
	let showModal = $state(false);
	
	function handleSearch(searchTerm) {
		console.log('Buscando:', searchTerm);
		// Here you would typically make an API call
		// For now, we'll just show all products or filter sample ones
		filteredProducts = products;
	}
	
	function handleProductClick(product) {
		selectedProduct = product;
		showModal = true;
	}
	
	function handleOrderConfirm(product) {
		console.log('Pedido confirmado para:', product.name);
		// Here you would handle the order submission
		alert(`Pedido confirmado: ${product.name}`);
	}
	
	function handleOrderCancel() {
		console.log('Pedido cancelado');
	}
</script>

<div class="min-h-screen bg-gray-50">
	<Navbar />
	<HeroSection onSearch={handleSearch} />
	<ProductGrid products={filteredProducts} onProductClick={handleProductClick} />
	<OrderModal 
		bind:isOpen={showModal} 
		product={selectedProduct} 
		onConfirm={handleOrderConfirm} 
		onCancel={handleOrderCancel} 
	/>
</div>
