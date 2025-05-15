<script>
	import '../app.css';
	import { fade, slide } from 'svelte/transition';

	let { children } = $props();
	let menuOpen = $state(false);
	let visible = $state(false);
	let showDropdown = $state(false);
	let hideTimeout;

	function openDropdown() {
		clearTimeout(hideTimeout);
		showDropdown = true;
	}

	function delayedCloseDropdown() {
		hideTimeout = setTimeout(() => {
			showDropdown = false;
		}, 300);
	}

	$effect(() => {
		requestAnimationFrame(() => {
			visible = true;
		});
	});
</script>

<nav class="flex items-center justify-between px-6 py-5 bg-[#374993] text-white relative z-10">
	<!-- Logo Reveal Wrapper -->
	<div class="overflow-hidden h-16 w-16">
		<img
			src="/logo.png"
			alt="Surcos Logo"
			class="w-full h-auto transform transition-transform duration-[1500ms] ease-out"
			class:translate-y-full={!visible}
			class:translate-y-0={visible}
		/>
	</div>

	<!-- Mobile Menu Toggle -->
	<button
		class="text-3xl md:hidden"
		onclick={() => menuOpen = !menuOpen}
		aria-expanded={menuOpen}
		aria-label="Toggle navigation menu"
	>
		☰
	</button>

	<!-- Navigation Links -->
	<ul class="flex gap-8 items-center text-lg font-['Space_Grotesk'] relative">
		<!-- Secciones Dropdown (Hover with 1.5s delay on close) -->
		<li
			class="relative"
			onmouseenter={openDropdown}
			onmouseleave={delayedCloseDropdown}
		>
			<span class="cursor-pointer hover:underline">Secciones</span>
			{#if showDropdown}
			<ul
				in:slide={{ y: 10, duration: 250 }}
				out:slide={{ y: 10, duration: 300 }}
				class="absolute flex flex-col bg-[#374993] text-white mt-3 p-3 rounded-md shadow-lg w-48 z-10 text-base space-y-1"
			>

					<li><a href="/justicia" class="hover:underline py-1">Justicia</a></li>
					<li><a href="/desarrollo" class="hover:underline py-1">Desigualdad</a></li>
					<li><a href="/cultura" class="hover:underline py-1">Cultura</a></li>
					<li><a href="/politica" class="hover:underline py-1">Política</a></li>
					<li><a href="/medio-ambiente" class="hover:underline py-1">Ambiente</a></li>
				</ul>
			{/if}
		</li>

		<!-- Standalone Links -->
		<li><a href="/nosotros" class="hover:underline">Nosotros</a></li>
		<li><a href="/contacto" class="hover:underline">Contacto</a></li>
	</ul>
</nav>

<main>
	{@render children()}
</main>
