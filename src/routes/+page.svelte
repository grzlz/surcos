<script>
	let menuOpen = $state(false);
</script>

<nav class="flex items-center justify-between px-6 py-4 bg-[#374993] text-white relative z-10">
	<div class="text-xl font-bold uppercase font-['Special_Gothic_Condensed_One']">surcos</div>
	<button class="text-2xl md:hidden" onclick={() => menuOpen = !menuOpen}>☰</button>
	<ul class={`md:flex gap-6 absolute md:static top-full right-6 bg-[#374993] md:bg-transparent p-4 md:p-0 rounded-md md:rounded-none shadow-md md:shadow-none transition-all duration-300 ease-in-out ${menuOpen ? 'flex flex-col' : 'hidden'}`}>
		<li><a href="/justicia" class="font-['Space_Grotesk'] hover:underline">Justicia</a></li>
		<li><a href="/desarrollo" class="font-['Space_Grotesk'] hover:underline">Desigualdad</a></li>
		<li><a href="/cultura" class="font-['Space_Grotesk'] hover:underline">Cultura</a></li>
		<li><a href="/politica" class="font-['Space_Grotesk'] hover:underline">Política</a></li>
		<li><a href="/medio-ambiente" class="font-['Space_Grotesk'] hover:underline">Ambiente</a></li>
	</ul>
</nav>

<header class="text-center py-24 px-4 bg-gradient-to-br from-[#88378C] to-[#4F449E] text-white">
	<h1 class="text-4xl md:text-6xl font-['Special_Gothic_Condensed_One'] mb-4">Revista Digital Surcos</h1>
	<p class="text-lg md:text-xl">Periodismo de izquierda – Confrontativa. Inclusiva. Actual.</p>
</header>

<section class="max-w-3xl mx-auto px-4 py-16 text-center">
	<h2 class="text-2xl md:text-3xl text-[#3C8063] font-['Space_Grotesk'] mb-4">Nuestros Ejes</h2>
	<p class="text-base md:text-lg text-gray-700 leading-relaxed font-['DM_Sans']">
		Exploramos temas desde una perspectiva crítica: derechos humanos, desarrollo, cultura,
		política y más. Contribuimos a la transformación social con información, análisis y reflexión.
	</p>

    <button class="bg-sky-500 hover:bg-sky-700 active:bg-violet-700">Save changes</button>
</section>
