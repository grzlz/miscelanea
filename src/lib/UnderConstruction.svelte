<script>
	let { pageTitle = "Esta página", message = "Estamos trabajando en el sitio" } = $props();
</script>

<div class="min-h-screen bg-gradient-to-br from-amber-50 via-orange-50 to-amber-100 flex items-center justify-center p-4">
	<!-- Animated background elements -->
	<div class="absolute inset-0 overflow-hidden pointer-events-none">
		<div class="absolute top-20 left-20 w-40 h-40 bg-amber-400/20 rounded-full blur-3xl animate-pulse"></div>
		<div class="absolute bottom-20 right-20 w-56 h-56 bg-orange-400/20 rounded-full blur-3xl animate-pulse delay-1000"></div>
		<div class="absolute top-1/3 right-1/3 w-32 h-32 bg-yellow-400/20 rounded-full blur-2xl animate-bounce delay-500"></div>
	</div>

	<div class="relative z-10 text-center max-w-2xl mx-auto">
		<!-- Construction Icon -->
		<div class="mb-8 animate-bounce">
			<div class="mx-auto w-24 h-24 bg-gradient-to-r from-amber-600 to-orange-600 rounded-2xl flex items-center justify-center shadow-2xl">
				<svg class="w-12 h-12 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
					<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19.428 15.428a2 2 0 00-1.022-.547l-2.387-.477a6 6 0 00-3.86.517l-.318.158a6 6 0 01-3.86.517L6.05 15.21a2 2 0 00-1.806.547M8 4h8l-1 1v5.172a2 2 0 00.586 1.414l5 5c1.26 1.26.367 3.414-1.415 3.414H4.828c-1.782 0-2.674-2.154-1.414-3.414l5-5A2 2 0 009 10.172V5L8 4z"></path>
				</svg>
			</div>
		</div>

		<!-- Main Content -->
		<h1 class="text-4xl md:text-5xl font-bold text-gray-900 mb-4 animate-fade-in-up">
			{message}
		</h1>
		
		<p class="text-xl text-gray-600 mb-8 animate-fade-in-up delay-200">
			{pageTitle} estará disponible muy pronto
		</p>



		<!-- Back Home Button -->
		<div class="relative top-8 animate-fade-in-up delay-600">
			<a 
				href="/" 
				class="inline-flex items-center gap-3 bg-gradient-to-r from-amber-600 to-orange-600 text-white px-8 py-4 rounded-full font-semibold hover:from-amber-700 hover:to-orange-700 transition-all duration-300 transform hover:scale-105 shadow-lg hover:shadow-xl"
			>

				Volver al inicio
			</a>
		</div>

		<!-- Fun Elements -->
		<div class="mt-12 flex justify-center space-x-4 animate-fade-in-up delay-800">
			<div class="w-3 h-3 bg-amber-500 rounded-full animate-ping"></div>
			<div class="w-3 h-3 bg-orange-500 rounded-full animate-ping delay-100"></div>
			<div class="w-3 h-3 bg-yellow-500 rounded-full animate-ping delay-200"></div>
		</div>
	</div>
</div>

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
	
	@keyframes progress {
		0% { width: 0%; }
		50% { width: 70%; }
		100% { width: 85%; }
	}
	
	.animate-fade-in-up {
		animation: fade-in-up 0.8s ease-out forwards;
	}
	
	.animate-progress {
		animation: progress 3s ease-in-out infinite;
	}
	
	.delay-200 {
		animation-delay: 0.2s;
		opacity: 0;
	}
	
	.delay-400 {
		animation-delay: 0.4s;
		opacity: 0;
	}
	
	.delay-600 {
		animation-delay: 0.6s;
		opacity: 0;
	}
	
	.delay-800 {
		animation-delay: 0.8s;
		opacity: 0;
	}
</style>