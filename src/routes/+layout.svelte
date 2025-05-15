<script>
	import '../app.css';
	import { slide } from 'svelte/transition';

	let { children } = $props();
	let menuOpen = $state(false);
	let seccionesOpen = $state(false); 
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
	{#if menuOpen}
		<ul
			in:slide={{ y: 10, duration: 250 }}
			out:slide={{ y: 10, duration: 250 }}
			class="flex flex-col md:flex md:flex-row gap-6 items-start md:items-center text-lg font-['Space_Grotesk'] absolute md:static top-full right-6 bg-[#374993] md:bg-transparent p-4 md:p-0 rounded-md md:rounded-none shadow-md md:shadow-none z-10 w-64 md:w-auto"
		>
			<!-- Desktop Secciones Dropdown (hover) -->
			<li
				class="relative hidden md:block"
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

			<!-- Mobile Secciones Toggle (click) -->
			<li class="block md:hidden">
				<button
					onclick={() => seccionesOpen = !seccionesOpen}
					class="hover:underline focus:outline-none"
				>
					Secciones {seccionesOpen ? '▲' : '▼'}
				</button>
				{#if seccionesOpen}
					<ul
						in:slide={{ y: 10, duration: 250 }}
						out:slide={{ y: 10, duration: 200 }}
						class="mt-2 ml-4 space-y-1"
					>
						<li><a href="/justicia" class="hover:underline">Justicia</a></li>
						<li><a href="/desarrollo" class="hover:underline">Desigualdad</a></li>
						<li><a href="/cultura" class="hover:underline">Cultura</a></li>
						<li><a href="/politica" class="hover:underline">Política</a></li>
						<li><a href="/medio-ambiente" class="hover:underline">Ambiente</a></li>
					</ul>
				{/if}
			</li>

			<!-- Standalone links -->
			<li><a href="/nosotros" class="hover:underline">Nosotros</a></li>
			<li><a href="/contacto" class="hover:underline">Contacto</a></li>
		</ul>
	{/if}
</nav>

<main>
	{@render children()}
</main>
