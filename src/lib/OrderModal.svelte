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
		class="fixed inset-0 bg-black/60 backdrop-blur-sm flex items-center justify-center p-4 z-50 animate-fade-in"
		on:click={handleBackdropClick}
		role="dialog"
		aria-modal="true"
	>
		<div class="bg-white rounded-2xl max-w-lg w-full p-0 relative shadow-2xl animate-slide-up transform-gpu">
			<!-- Header with gradient -->
			<div class="bg-gradient-to-r from-amber-600 to-orange-600 p-6 rounded-t-2xl relative">
				<button 
					on:click={handleCancel}
					class="absolute top-4 right-4 text-white/80 hover:text-white transition-colors duration-200"
					aria-label="Cerrar"
				>
					<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
					</svg>
				</button>
				<h3 class="text-2xl font-bold text-white">Confirmar Pedido</h3>
				<p class="text-amber-100 mt-1">Revisa los detalles antes de confirmar</p>
			</div>
			
			<div class="p-6">
			
				<div class="mb-6">
					<div class="flex gap-4 p-4 bg-gray-50 rounded-xl">
						<div class="w-24 h-24 bg-gradient-to-br from-gray-100 to-gray-200 rounded-xl overflow-hidden flex-shrink-0 shadow-md">
							<img 
								src={product.image} 
								alt={product.name}
								class="w-full h-full object-cover"
							>
						</div>
						<div class="flex-1">
							<h4 class="font-bold text-xl text-gray-900 mb-1">{product.name}</h4>
							<p class="text-gray-600 text-sm mb-2">{product.description}</p>
							<p class="text-2xl font-bold bg-gradient-to-r from-amber-600 to-orange-600 bg-clip-text text-transparent">{product.price}</p>
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
			
				<div class="flex gap-4 pt-4 border-t border-gray-100">
					<button 
						on:click={handleCancel}
						class="flex-1 bg-gray-100 text-gray-700 font-semibold py-4 px-6 rounded-xl hover:bg-gray-200 transition-all duration-300 transform hover:scale-105"
					>
						Cancelar
					</button>
					<button 
						on:click={handleConfirm}
						class="flex-1 bg-gradient-to-r from-amber-600 to-orange-600 text-white font-semibold py-4 px-6 rounded-xl hover:from-amber-700 hover:to-orange-700 transition-all duration-300 transform hover:scale-105 shadow-lg hover:shadow-xl"
					>
						🛒 Confirmar Pedido
					</button>
				</div>
			</div>
		</div>
	</div>
{/if}

<style>
	@keyframes fade-in {
		from { opacity: 0; }
		to { opacity: 1; }
	}
	
	@keyframes slide-up {
		from { 
			opacity: 0;
			transform: translateY(30px) scale(0.95);
		}
		to { 
			opacity: 1;
			transform: translateY(0) scale(1);
		}
	}
	
	.animate-fade-in {
		animation: fade-in 0.3s ease-out;
	}
	
	.animate-slide-up {
		animation: slide-up 0.4s ease-out;
	}
</style>