<script>
	import { slide } from 'svelte/transition';

	let { children } = $props();

	let menuOpen = $state(false);
	let showDropdown = $state(false);

	const sections = [
		{
			href: '/justicia',
			label: 'Justicia',
			description: 'Derechos, ciudadanía y acceso a la justicia',
			color: '#3C8063'
		},
		{
			href: '/desarrollo',
			label: 'Desigualdad',
			description: 'Economía popular, trabajo y territorios',
			color: '#88378C'
		},
		{
			href: '/cultura',
			label: 'Cultura',
			description: 'Artes, identidad y memorias en disputa',
			color: '#4F449E'
		},
		{
			href: '/politica',
			label: 'Política',
			description: 'Poder, democracia y horizontes colectivos',
			color: '#C44949'
		},
		{
			href: '/medio-ambiente',
			label: 'Ambiente',
			description: 'Clima, extractivismo y justicia ambiental',
			color: '#B13E3E'
		}
	];

	const mainLinks = [
		{ href: '/nosotros', label: 'Nosotros' },
		{ href: '/contacto', label: 'Contacto' }
	];

	$effect(() => {
		if (!menuOpen || typeof window === 'undefined') return;

		const handleKeydown = (event) => {
			if (event.key === 'Escape') {
				menuOpen = false;
			}
		};

		window.addEventListener('keydown', handleKeydown);
		return () => window.removeEventListener('keydown', handleKeydown);
	});
</script>

<div class="relative min-h-screen bg-[#f5efe6] text-slate-900">
	<nav class="pointer-events-none fixed inset-x-0 top-0 z-50">
		<div class="pointer-events-auto mx-auto max-w-6xl px-4 sm:px-6 lg:px-8">
			<div
				class="mt-6 flex items-center justify-between rounded-3xl border border-slate-200/80 bg-white/90 px-5 py-4 shadow-lg shadow-slate-400/30 backdrop-blur"
			>
				<a href="/" class="flex items-center gap-3">
					<span
						class="inline-flex h-12 w-12 items-center justify-center rounded-2xl border border-slate-200 bg-white"
					>
						<img src="/logo.png" alt="Surcos" class="h-9 w-9" />
					</span>
					<div class="flex flex-col">
						<span class="font-['Space_Grotesk'] text-lg font-semibold tracking-tight text-slate-900"
							>Surcos</span
						>
						<span class="font-['DM_Sans'] text-xs tracking-[0.32em] text-slate-500 uppercase"
							>Revista Digital</span
						>
					</div>
				</a>

				<div class="hidden items-center gap-2 lg:flex">
					<div
						class="relative"
						role="presentation"
						onmouseenter={() => (showDropdown = true)}
						onmouseleave={() => (showDropdown = false)}
						onfocusin={() => (showDropdown = true)}
						onfocusout={() => (showDropdown = false)}
					>
						<button
							class="inline-flex items-center gap-2 rounded-full border border-slate-200 bg-white px-4 py-2 text-sm font-medium tracking-wide text-slate-700 transition hover:border-slate-400 hover:bg-slate-100 hover:text-slate-900"
							aria-haspopup="true"
							aria-controls="secciones-menu"
							aria-expanded={showDropdown}
						>
							<span>Secciones</span>
							<svg
								class={`h-4 w-4 transition-transform ${showDropdown ? 'rotate-180' : ''}`}
								viewBox="0 0 24 24"
								fill="none"
								stroke="currentColor"
								stroke-width="1.5"
							>
								<path d="M6 9l6 6 6-6" stroke-linecap="round" stroke-linejoin="round"></path>
							</svg>
						</button>

						{#if showDropdown}
							<div
								class="absolute right-0 z-30 mt-4 w-96 rounded-3xl border border-slate-200 bg-white p-4 shadow-xl shadow-slate-400/30"
								id="secciones-menu"
							>
								<div class="grid gap-3">
									{#each sections as section (section.href)}
										<a
											href={section.href}
											class="group flex items-start gap-3 rounded-2xl border border-slate-200 bg-white px-4 py-3 transition hover:-translate-y-0.5 hover:border-slate-400 hover:shadow-md"
											style={`box-shadow: 0 12px 24px -18px ${section.color}55;`}
										>
											<span
												class="mt-1 inline-flex h-9 w-9 flex-shrink-0 items-center justify-center rounded-2xl border border-slate-200"
												style={`background:${section.color}15; color:${section.color};`}
											>
												<span class="h-2.5 w-2.5 rounded-full" style={`background:${section.color}`}
												></span>
											</span>
											<span class="flex flex-col">
												<span class="font-['Space_Grotesk'] text-sm font-semibold text-slate-900"
													>{section.label}</span
												>
												<span class="font-['DM_Sans'] text-xs text-slate-600"
													>{section.description}</span
												>
											</span>
										</a>
									{/each}
								</div>
							</div>
						{/if}
					</div>

					{#each mainLinks as link (link.href)}
						<a
							href={link.href}
							class="rounded-full border border-transparent px-4 py-2 text-sm font-medium tracking-wide text-slate-700 transition hover:text-slate-900 hover:underline"
						>
							{link.label}
						</a>
					{/each}

					<a
						href="/newsletter"
						class="rounded-full bg-slate-900 px-4 py-2 text-sm font-semibold tracking-[0.18em] text-white uppercase transition hover:bg-slate-700"
					>
						Newsletter
					</a>
				</div>

				<button
					class="inline-flex h-11 w-11 items-center justify-center rounded-full border border-slate-200 bg-white text-slate-700 transition hover:border-slate-400 hover:bg-slate-100 lg:hidden"
					onclick={() => (menuOpen = !menuOpen)}
					aria-label="Abrir menú"
					aria-expanded={menuOpen}
				>
					<svg
						class={`h-5 w-5 transition-transform ${menuOpen ? 'rotate-90' : ''}`}
						viewBox="0 0 24 24"
						fill="none"
						stroke="currentColor"
						stroke-width="1.5"
					>
						{#if menuOpen}
							<path d="M6 6l12 12M6 18L18 6" stroke-linecap="round"></path>
						{:else}
							<path d="M4 7h16M4 12h16M4 17h16" stroke-linecap="round"></path>
						{/if}
					</svg>
				</button>
			</div>
		</div>
	</nav>

	{#if menuOpen}
		<div class="fixed inset-0 z-40 lg:hidden">
			<button
				type="button"
				class="absolute inset-0 h-full w-full cursor-pointer bg-slate-900/20 backdrop-blur"
				aria-label="Cerrar menú"
				onclick={() => (menuOpen = false)}
			></button>
			<div class="relative mx-4 mt-28" in:slide={{ duration: 250 }} out:slide={{ duration: 200 }}>
				<div
					class="space-y-6 rounded-3xl border border-slate-200 bg-white p-6 shadow-xl shadow-slate-400/30"
				>
					<div class="space-y-4">
						<span class="font-['DM_Sans'] text-xs tracking-[0.28em] text-slate-500 uppercase"
							>Secciones</span
						>
						<div class="grid gap-3">
							{#each sections as section (section.href)}
								<a
									href={section.href}
									class="flex items-center justify-between rounded-2xl border border-slate-200 bg-white px-4 py-3 transition hover:-translate-y-0.5 hover:border-slate-400 hover:shadow-md"
									style={`box-shadow: 0 12px 24px -18px ${section.color}55;`}
									onclick={() => (menuOpen = false)}
								>
									<div class="flex items-center gap-3">
										<span
											class="inline-flex h-9 w-9 items-center justify-center rounded-2xl border border-slate-200"
											style={`background:${section.color}15;`}
										>
											<span class="h-2.5 w-2.5 rounded-full" style={`background:${section.color}`}
											></span>
										</span>
										<div>
											<p class="font-['Space_Grotesk'] text-sm font-semibold text-slate-900">
												{section.label}
											</p>
											<p class="font-['DM_Sans'] text-xs text-slate-600">{section.description}</p>
										</div>
									</div>
									<svg
										class="h-4 w-4 text-slate-400"
										viewBox="0 0 24 24"
										fill="none"
										stroke="currentColor"
										stroke-width="1.5"
									>
										<path d="M9 6l6 6-6 6" stroke-linecap="round" stroke-linejoin="round"></path>
									</svg>
								</a>
							{/each}
						</div>
					</div>

					<div class="space-y-3">
						<span class="font-['DM_Sans'] text-xs tracking-[0.28em] text-slate-500 uppercase"
							>Más</span
						>
						<div class="grid gap-2">
							{#each mainLinks as link (link.href)}
								<a
									href={link.href}
									class="rounded-2xl border border-slate-200 bg-white px-4 py-3 text-sm font-medium text-slate-700 transition hover:border-slate-400 hover:bg-slate-100 hover:text-slate-900"
									onclick={() => (menuOpen = false)}
								>
									{link.label}
								</a>
							{/each}
							<a
								href="/newsletter"
								class="rounded-2xl bg-slate-900 px-4 py-3 text-center text-sm font-semibold tracking-[0.18em] text-white uppercase transition hover:bg-slate-700"
								onclick={() => (menuOpen = false)}
							>
								Newsletter
							</a>
						</div>
					</div>
				</div>
			</div>
		</div>
	{/if}

	<main
		class="relative flex min-h-screen flex-col bg-gradient-to-br from-[#f8f3ec] via-[#f5efe6] to-[#f1e7db] pt-32"
	>
		{@render children()}

		<footer class="mt-auto border-t border-slate-200/70 bg-white/70">
			<div class="mx-auto max-w-6xl px-4 py-16 sm:px-6 lg:px-8">
				<div class="grid gap-12 md:grid-cols-[1.2fr,0.8fr]">
					<div class="space-y-6">
						<a href="/" class="inline-flex items-center gap-3">
							<span
								class="inline-flex h-12 w-12 items-center justify-center rounded-2xl border border-slate-200 bg-white"
							>
								<img src="/logo.png" alt="Surcos" class="h-9 w-9" />
							</span>
							<div class="flex flex-col">
								<span
									class="font-['Space_Grotesk'] text-lg font-semibold tracking-tight text-slate-900"
									>Surcos</span
								>
								<span class="font-['DM_Sans'] text-xs tracking-[0.32em] text-slate-500 uppercase"
									>Periodismo de izquierda</span
								>
							</div>
						</a>
						<p class="max-w-xl font-['DM_Sans'] text-sm leading-relaxed text-slate-600">
							Historias, análisis y crónicas que atraviesan nuestros territorios. Una revista
							digital independiente que amplifica las voces que abren nuevos horizontes.
						</p>
						<div class="flex flex-wrap gap-3">
							{#each sections as section (section.href)}
								<span
									class="inline-flex items-center gap-2 rounded-full border border-slate-200 bg-white px-3 py-1 text-xs font-medium text-slate-600"
									style={`box-shadow: inset 0 0 0 1px ${section.color}55;`}
								>
									<span class="h-2 w-2 rounded-full" style={`background:${section.color}`}></span>
									{section.label}
								</span>
							{/each}
						</div>
					</div>
					<div class="grid gap-8 sm:grid-cols-2">
						<div class="space-y-4">
							<span class="font-['DM_Sans'] text-xs tracking-[0.28em] text-slate-500 uppercase"
								>Explorar</span
							>
							<div class="grid gap-3">
								{#each sections as section (section.href)}
									<a
										href={section.href}
										class="group flex items-center justify-between rounded-2xl border border-slate-200 bg-white px-4 py-3 text-sm font-medium text-slate-600 transition hover:-translate-y-0.5 hover:border-slate-400 hover:bg-slate-100 hover:text-slate-900"
									>
										<span>{section.label}</span>
										<svg
											class="h-4 w-4 text-slate-400 opacity-0 transition group-hover:text-slate-600 group-hover:opacity-100"
											viewBox="0 0 24 24"
											fill="none"
											stroke="currentColor"
											stroke-width="1.5"
										>
											<path d="M9 6l6 6-6 6" stroke-linecap="round" stroke-linejoin="round"></path>
										</svg>
									</a>
								{/each}
							</div>
						</div>
						<div class="space-y-4">
							<span class="font-['DM_Sans'] text-xs tracking-[0.28em] text-slate-500 uppercase"
								>Contacto</span
							>
							<div class="space-y-3">
								{#each mainLinks as link (link.href)}
									<a
										href={link.href}
										class="block rounded-2xl border border-slate-200 bg-white px-4 py-3 text-sm font-medium text-slate-700 transition hover:border-slate-400 hover:bg-slate-100 hover:text-slate-900"
									>
										{link.label}
									</a>
								{/each}
								<a
									href="mailto:contacto@surcos.com"
									class="block rounded-2xl border border-slate-200 bg-white px-4 py-3 text-sm font-medium text-slate-700 transition hover:border-slate-400 hover:bg-slate-100 hover:text-slate-900"
								>
									contacto@surcos.com
								</a>
							</div>
						</div>
					</div>
				</div>
				<div
					class="mt-12 border-t border-slate-200/80 pt-6 text-center font-['DM_Sans'] text-xs tracking-[0.32em] text-slate-500 uppercase"
				>
					© {new Date().getFullYear()} Surcos. Todos los derechos reservados.
				</div>
			</div>
		</footer>
	</main>
</div>
