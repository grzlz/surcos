<script>
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
		if (typeof window !== 'undefined') {
			requestIdleCallback(() => {
				visible = true;
			});
		}
	});

    let sections = [
        { href: '/justicia', label: 'Justicia', color: '#3C8063' },
        { href: '/desarrollo', label: 'Desigualdad', color: '#88378C' },
        { href: '/cultura', label: 'Cultura', color: '#4F449E' },
        { href: '/politica', label: 'Política', color: '#C44949' },
        { href: '/medio-ambiente', label: 'Ambiente', color: '#B13E3E' }
    ];
</script>

<nav class="bg-[#374993] text-white shadow-md sticky top-0 z-50 backdrop-blur-sm">
	<div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
		<div class="flex justify-between items-center h-16">
			<!-- Logo -->
				<div class="overflow-hidden h-14 w-14 mr-3">
					<img
						src="/logo.png"
						alt="Surcos Logo"
						class="transition-all duration-1000 ease-out hover:scale-110"
						class:translate-y-full={!visible}
						class:translate-y-0={visible}
					/>
				</div>

			<!-- Desktop Navigation -->
			<div class="hidden md:flex items-center space-x-6">
				<!-- Dropdown Menu -->
				<div
					class="relative group"
                    role="button"
                    tabindex="0"
					onmouseenter={openDropdown}
					onmouseleave={delayedCloseDropdown}
				>
					<button
						class="flex items-center px-3 py-2 rounded-md hover:bg-white/10 transition font-medium font-['Space_Grotesk']"
						aria-haspopup="true"
						aria-controls="dropdown-menu"
						aria-expanded={showDropdown}
					>
						<span>Secciones</span>
						<svg class={`w-4 h-4 ml-1 transition-transform duration-200 ${showDropdown ? 'rotate-180' : ''}`} fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"></path>
						</svg>
					</button>

					{#if showDropdown}
						<div
							in:slide={{ y: -10, duration: 250 }}
							out:slide={{ y: -10, duration: 200 }}
							class="absolute top-full left-0 mt-2 w-56 bg-white rounded-xl shadow-xl border border-gray-100 z-20"
							id="dropdown-menu"
						>
							<div class="py-2">
								{#each sections as item}
									<a href={item.href} class="flex items-center px-4 py-3 text-gray-700 hover:bg-[#374993] hover:text-white transition group">
										<div class={`w-8 h-8 rounded-full flex items-center justify-center mr-3`} style={`background-color: ${item.color}1A`}>
											<div class="w-4 h-4 rounded-full" style={`background-color: ${item.color}`}></div>
										</div>
										<span class="font-['DM_Sans'] font-medium">{item.label}</span>
									</a>
								{/each}
							</div>
						</div>
					{/if}
				</div>

				<a href="/nosotros" class="px-3 py-2 rounded-md hover:bg-white/10 transition font-medium font-['Space_Grotesk']">Nosotros</a>
				<a href="/contacto" class="px-3 py-2 rounded-md hover:bg-white/10 transition font-medium font-['Space_Grotesk']">Contacto</a>
			</div>

			<!-- Mobile Menu Button -->
			<button
				class="md:hidden p-2 rounded-md hover:bg-white/10 transition focus:outline-none"
				onclick={() => (menuOpen = !menuOpen)}
				aria-label="Toggle mobile menu"
				aria-expanded={menuOpen}
			>
				<svg class={`w-6 h-6 transition-transform duration-300 ${menuOpen ? 'rotate-90' : ''}`} fill="none" stroke="currentColor" viewBox="0 0 24 24">
					<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
				</svg>
			</button>
		</div>
	</div>

	<!-- Mobile Menu -->
	{#if menuOpen}
		<div
			in:slide={{ duration: 300 }}
			out:slide={{ duration: 200 }}
			class="md:hidden bg-[#2c3e50] border-t border-white/10"
		>
			<div class="px-4 py-4 space-y-3">
				<!-- Mobile Dropdown -->
				<div>
					<button
						onclick={() => (seccionesOpen = !seccionesOpen)}
						class="flex justify-between items-center w-full px-3 py-2 rounded-md hover:bg-white/10 transition font-medium font-['Space_Grotesk']"
						aria-haspopup="true"
						aria-expanded={seccionesOpen}
					>
						<span>Secciones</span>
						<svg class={`w-5 h-5 transition-transform ${seccionesOpen ? 'rotate-180' : ''}`} fill="none" stroke="currentColor" viewBox="0 0 24 24">
							<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"></path>
						</svg>
					</button>

					{#if seccionesOpen}
						<div in:slide={{ duration: 200 }} out:slide={{ duration: 150 }} class="mt-2 ml-3 space-y-1">
							{#each [
								{ href: '/justicia', label: 'Justicia' },
								{ href: '/desarrollo', label: 'Desigualdad' },
								{ href: '/cultura', label: 'Cultura' },
								{ href: '/politica', label: 'Política' },
								{ href: '/medio-ambiente', label: 'Ambiente' }
							] as item}
								<a href={item.href} class="block px-3 py-2 text-white/80 hover:text-white hover:bg-white/5 rounded-md font-['DM_Sans']">{item.label}</a>
							{/each}
						</div>
					{/if}
				</div>

				<a href="/nosotros" class="block px-3 py-2 text-white hover:bg-white/10 rounded-md font-medium font-['Space_Grotesk']">Nosotros</a>
				<a href="/contacto" class="block px-3 py-2 text-white hover:bg-white/10 rounded-md font-medium font-['Space_Grotesk']">Contacto</a>
			</div>
		</div>
	{/if}
</nav>

<main class="flex flex-col min-h-screen">
	{@render children()}
    <footer class="mt-auto">
        <div class="bg-gradient-to-r from-[#C44949] to-[#B13E3E] text-white py-10">
            <div class="max-w-4xl mx-auto px-4">
                <div class="text-center">
                    <p class="text-sm md:text-base font-['DM_Sans'] opacity-90">
                        © {new Date().getFullYear()} Surcos. Todos los derechos reservados.
                    </p>
                </div>
            </div>
        </div>
    </footer>
</main>


