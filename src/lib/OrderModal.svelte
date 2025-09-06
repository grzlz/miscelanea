<script>
	let { isOpen = $bindable(false), product = null, onConfirm = () => {}, onCancel = () => {} } = $props();
	
	function handleConfirm() {
		onConfirm(product);
		isOpen = false;
	}
	
	function handleCancel() {
		onCancel();
		isOpen = false;
	}
	
	function handleBackdropClick(event) {
		if (event.target === event.currentTarget) {
			handleCancel();
		}
	}
</script>

{#if isOpen && product}
	<div 
		class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4 z-50"
		on:click={handleBackdropClick}
		role="dialog"
		aria-modal="true"
	>
		<div class="bg-white rounded-lg max-w-md w-full p-6 relative">
			<button 
				on:click={handleCancel}
				class="absolute top-4 right-4 text-gray-400 hover:text-gray-600"
				aria-label="Cerrar"
			>
				<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
					<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
				</svg>
			</button>
			
			<h3 class="text-2xl font-bold text-gray-900 mb-4">Confirmar Pedido</h3>
			
			<div class="mb-6">
				<div class="flex gap-4">
					<div class="w-20 h-20 bg-gray-100 rounded-lg overflow-hidden flex-shrink-0">
						<img 
							src={product.image} 
							alt={product.name}
							class="w-full h-full object-cover"
						>
					</div>
					<div class="flex-1">
						<h4 class="font-semibold text-lg text-gray-900">{product.name}</h4>
						<p class="text-gray-600 text-sm mb-1">{product.description}</p>
						<p class="text-xl font-bold text-amber-600">{product.price}</p>
					</div>
				</div>
			</div>
			
			<div class="mb-6">
				<label class="block text-sm font-medium text-gray-700 mb-2">
					Cantidad
				</label>
				<input 
					type="number" 
					min="1" 
					value="1"
					class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-amber-500"
				>
			</div>
			
			<div class="mb-6">
				<label class="block text-sm font-medium text-gray-700 mb-2">
					Notas adicionales (opcional)
				</label>
				<textarea 
					placeholder="Instrucciones especiales, horario de entrega, etc."
					rows="3"
					class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-amber-500 resize-none"
				></textarea>
			</div>
			
			<div class="flex gap-3">
				<button 
					on:click={handleConfirm}
					class="flex-1 bg-amber-600 text-white font-semibold py-3 px-4 rounded-md hover:bg-amber-700 transition-colors"
				>
					Confirmar Pedido
				</button>
				<button 
					on:click={handleCancel}
					class="flex-1 bg-gray-200 text-gray-800 font-semibold py-3 px-4 rounded-md hover:bg-gray-300 transition-colors"
				>
					Cancelar
				</button>
			</div>
		</div>
	</div>
{/if}