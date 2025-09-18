<script>
	const sectionCards = [
		{
			title: 'Justicia',
			accent: '#3C8063',
			description:
				'Seguimos los juicios, políticas públicas y luchas territoriales que garantizan derechos y reparaciones.',
			href: '/justicia'
		},
		{
			title: 'Desigualdad',
			accent: '#88378C',
			description:
				'Economía popular, redes comunitarias y nuevas formas de organización frente a la concentración.',
			href: '/desarrollo'
		},
		{
			title: 'Cultura',
			accent: '#4F449E',
			description:
				'Expresiones artísticas, memoria y lenguajes emergentes que expanden lo posible.',
			href: '/cultura'
		},
		{
			title: 'Política',
			accent: '#C44949',
			description:
				'Crónicas, análisis y protagonistas de los movimientos que disputan el sentido de lo público.',
			href: '/politica'
		},
		{
			title: 'Ambiente',
			accent: '#B13E3E',
			description:
				'Clima, extractivismos y alternativas desde los territorios para defender lo común.',
			href: '/medio-ambiente'
		}
	];

	const featureHighlights = [
		{
			eyebrow: 'Crónica destacada',
			title: 'Cuando la justicia llega tarde: historias mínimas desde los barrios populares',
			description:
				'Un recorrido por testimonios que reconstruyen cómo se teje la esperanza ante la demora del Estado.',
			accent: '#3C8063'
		},
		{
			eyebrow: 'Entrevista exclusiva',
			title: 'Tecnopolítica en disputa: imaginación colectiva para gobernar lo digital',
			description:
				'Conversamos con investigadoras y militantes que proponen regulaciones democráticas y abiertas.',
			accent: '#88378C'
		}
	];

	const editorialNotes = [
		{
			title: 'Radar de lecturas imprescindibles',
			description: 'Un mapa curado de columnas y podcasts que dialogan con nuestros territorios.',
			accent: '#4F449E'
		},
		{
			title: 'Mirada federal',
			description:
				'Una cobertura itinerante que acompaña luchas, celebraciones y resistencias en todo el país.',
			accent: '#C44949'
		},
		{
			title: 'Agenda verde',
			description:
				'Investigaciones y datos para actuar frente a la crisis climática desde la justicia social.',
			accent: '#B13E3E'
		}
	];
</script>

<section
	class="relative isolate overflow-hidden bg-gradient-to-br from-[#f9f2e8] via-[#f6efe6] to-[#f2eadf]"
>
	<div class="mx-auto flex max-w-6xl flex-col gap-12 px-6 pt-36 pb-24 sm:px-6 lg:px-8 lg:pt-40">
		<div class="grid items-end gap-14 lg:grid-cols-[1.25fr,0.75fr]">
			<div class="space-y-8 text-left">
				<span
					class="inline-flex items-center gap-2 rounded-full border border-slate-200 bg-white px-4 py-1 text-xs font-semibold tracking-[0.28em] text-slate-500 uppercase"
				>
					Nueva temporada
				</span>
				<h1
					class="font-['Space_Grotesk'] text-4xl leading-tight font-semibold text-slate-900 sm:text-5xl lg:text-6xl"
				>
					Periodismo que abre caminos para imaginar otros futuros posibles.
				</h1>
				<p class="max-w-2xl font-['DM_Sans'] text-base leading-relaxed text-slate-600 sm:text-lg">
					Surcos es una revista digital que explora los cruces entre justicia social, cultura,
					política y ambiente. Historias contadas con cuidado editorial, investigación rigurosa y
					estética audiovisual.
				</p>
				<div class="flex flex-wrap gap-4">
					<a
						href="/justicia"
						class="rounded-full border border-slate-900 px-6 py-3 text-xs font-semibold tracking-[0.28em] text-slate-900 uppercase transition hover:bg-slate-900 hover:text-white"
					>
						Explorar secciones
					</a>
					<a
						href="/newsletter"
						class="rounded-full bg-slate-900 px-6 py-3 text-xs font-semibold tracking-[0.28em] text-white uppercase transition hover:bg-slate-700"
					>
						Suscribirme
					</a>
				</div>
			</div>
			<div
				class="space-y-6 rounded-3xl border border-slate-200 bg-white p-8 shadow-lg shadow-slate-300/40"
			>
				<span class="font-['DM_Sans'] text-xs tracking-[0.32em] text-slate-500 uppercase"
					>Últimos lanzamientos</span
				>
				<div class="space-y-5">
					<div class="flex items-start gap-4">
						<span
							class="mt-1 inline-flex h-8 w-8 items-center justify-center rounded-2xl border border-slate-200"
							style="background:#88378C1a"
						>
							<span class="h-2.5 w-2.5 rounded-full" style="background:#88378C"></span>
						</span>
						<div class="space-y-1">
							<p class="font-['Space_Grotesk'] text-sm font-semibold text-slate-900">
								Dossier audiovisual: memorias del sur
							</p>
							<p class="font-['DM_Sans'] text-sm text-slate-600">
								Una serie de cortos que atraviesa músicas, rituales y luchas comunitarias.
							</p>
						</div>
					</div>
					<div class="flex items-start gap-4">
						<span
							class="mt-1 inline-flex h-8 w-8 items-center justify-center rounded-2xl border border-slate-200"
							style="background:#3C80631a"
						>
							<span class="h-2.5 w-2.5 rounded-full" style="background:#3C8063"></span>
						</span>
						<div class="space-y-1">
							<p class="font-['Space_Grotesk'] text-sm font-semibold text-slate-900">
								Informe interactivo: cartografías del cuidado
							</p>
							<p class="font-['DM_Sans'] text-sm text-slate-600">
								Datos, relatos y visualizaciones sobre redes feministas que sostienen la vida.
							</p>
						</div>
					</div>
					<div class="flex items-start gap-4">
						<span
							class="mt-1 inline-flex h-8 w-8 items-center justify-center rounded-2xl border border-slate-200"
							style="background:#C449491a"
						>
							<span class="h-2.5 w-2.5 rounded-full" style="background:#C44949"></span>
						</span>
						<div class="space-y-1">
							<p class="font-['Space_Grotesk'] text-sm font-semibold text-slate-900">
								Newsletter quincenal
							</p>
							<p class="font-['DM_Sans'] text-sm text-slate-600">
								Curaduría con lecturas recomendadas, agenda y avances de investigación.
							</p>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</section>

<section class="relative px-6 py-24 sm:px-6 lg:px-8">
	<div class="mx-auto max-w-6xl space-y-12">
		<div
			class="flex flex-col items-start gap-6 text-left lg:flex-row lg:items-end lg:justify-between"
		>
			<div>
				<span
					class="inline-flex items-center gap-2 rounded-full border border-slate-200 bg-white px-4 py-1 text-xs font-semibold tracking-[0.28em] text-slate-500 uppercase"
				>
					Nuestros ejes
				</span>
				<h2 class="mt-4 font-['Space_Grotesk'] text-3xl font-semibold text-slate-900 sm:text-4xl">
					Cinco secciones para narrar las fisuras y los deseos de una nueva época.
				</h2>
			</div>
			<p class="max-w-xl font-['DM_Sans'] text-sm leading-relaxed text-slate-600">
				Cada texto, foto, podcast y visualización se construye junto a las comunidades
				protagonistas. Investigamos, contamos historias y diseñamos experiencias digitales que
				acompañan los cambios en marcha.
			</p>
		</div>

		<div class="grid gap-6 md:grid-cols-2 xl:grid-cols-3">
			{#each sectionCards as card (card.href)}
				<a
					href={card.href}
					class="group relative flex h-full flex-col justify-between rounded-3xl border border-slate-200 bg-white p-7 shadow-md shadow-slate-300/30 transition hover:-translate-y-2 hover:border-slate-400 hover:shadow-xl"
					style={`box-shadow: 0 20px 40px -25px ${card.accent}55;`}
				>
					<div class="space-y-5">
						<span
							class="inline-flex items-center gap-2 rounded-full border border-slate-200 px-3 py-1 text-xs font-medium text-slate-600"
							style={`background:${card.accent}1a;`}
						>
							<span class="h-2 w-2 rounded-full" style={`background:${card.accent}`}></span>
							{card.title}
						</span>
						<p class="font-['Space_Grotesk'] text-xl font-semibold text-slate-900">
							{card.description}
						</p>
					</div>
					<span
						class="mt-8 inline-flex items-center gap-2 font-['DM_Sans'] text-sm font-medium text-slate-600 transition group-hover:gap-3 group-hover:text-slate-900"
					>
						Leer más
						<svg
							class="h-4 w-4"
							viewBox="0 0 24 24"
							fill="none"
							stroke="currentColor"
							stroke-width="1.5"
						>
							<path d="M9 6l6 6-6 6" stroke-linecap="round" stroke-linejoin="round"></path>
						</svg>
					</span>
				</a>
			{/each}
		</div>
	</div>
</section>

<section class="relative overflow-hidden px-6 pb-24 sm:px-6 lg:px-8">
	<div class="mx-auto max-w-6xl">
		<div class="grid gap-12 lg:grid-cols-[1.1fr,0.9fr]">
			<div
				class="space-y-8 rounded-3xl border border-slate-200 bg-white p-10 shadow-lg shadow-slate-300/40"
			>
				{#each featureHighlights as feature (feature.title)}
					<article
						class="rounded-3xl border border-slate-200 bg-[#f5efe6] p-8 transition hover:-translate-y-1 hover:border-slate-400 hover:shadow-lg"
						style={`box-shadow: 0 18px 40px -24px ${feature.accent}55;`}
					>
						<span
							class="font-['DM_Sans'] text-xs tracking-[0.28em] uppercase"
							style={`letter-spacing:0.28em; color:${feature.accent};`}
						>
							{feature.eyebrow}
						</span>
						<h3
							class="mt-4 font-['Space_Grotesk'] text-2xl font-semibold text-slate-900 sm:text-3xl"
						>
							{feature.title}
						</h3>
						<p class="mt-3 font-['DM_Sans'] text-sm leading-relaxed text-slate-600">
							{feature.description}
						</p>
					</article>
				{/each}
			</div>
			<div class="space-y-8">
				<div class="rounded-3xl border border-slate-200 bg-white p-8 shadow-lg shadow-slate-300/40">
					<span class="font-['DM_Sans'] text-xs tracking-[0.32em] text-slate-500 uppercase"
						>Editorial</span
					>
					<h3 class="mt-4 font-['Space_Grotesk'] text-2xl font-semibold text-slate-900">
						Tres líneas que guían nuestra mirada.
					</h3>
					<div class="mt-8 space-y-6">
						{#each editorialNotes as note (note.title)}
							<div
								class="rounded-2xl border border-slate-200 bg-[#f5efe6] p-6"
								style={`box-shadow: 0 14px 30px -24px ${note.accent}55;`}
							>
								<span
									class="inline-flex items-center gap-2 rounded-full border border-slate-200 px-3 py-1 text-xs font-medium text-slate-600"
									style={`background:${note.accent}1a;`}
								>
									<span class="h-2 w-2 rounded-full" style={`background:${note.accent}`}></span>
									{note.title}
								</span>
								<p class="mt-4 font-['DM_Sans'] text-sm leading-relaxed text-slate-600">
									{note.description}
								</p>
							</div>
						{/each}
					</div>
				</div>
				<div
					class="rounded-3xl border border-slate-200 bg-[#f5efe6] p-8 text-center shadow-lg shadow-slate-300/40"
				>
					<h3 class="font-['Space_Grotesk'] text-2xl font-semibold text-slate-900">
						Sumate a nuestra comunidad
					</h3>
					<p class="mt-3 font-['DM_Sans'] text-sm leading-relaxed text-slate-600">
						Recibí adelantos, materiales descargables y convocatorias abiertas para participar en
						nuestras coberturas colaborativas.
					</p>
					<a
						href="/newsletter"
						class="mt-8 inline-flex items-center justify-center gap-2 rounded-full bg-slate-900 px-6 py-3 text-xs font-semibold tracking-[0.28em] text-white uppercase transition hover:bg-slate-700"
					>
						Suscribirme
						<svg
							class="h-4 w-4"
							viewBox="0 0 24 24"
							fill="none"
							stroke="currentColor"
							stroke-width="1.5"
						>
							<path d="M9 6l6 6-6 6" stroke-linecap="round" stroke-linejoin="round"></path>
						</svg>
					</a>
				</div>
			</div>
		</div>
	</div>
</section>
