<script lang="ts">
	import * as Carousel from '$lib/components/ui/carousel/index.js';
	import { ArrowRight, ArrowLeft } from 'lucide-svelte';

	const sections = [
		{
			id: 'productos',
			title: 'Productos',
			description: 'Catálogo completo de soluciones para tu espacio.',
			image:
				'https://images.unsplash.com/photo-1562259929-b4e1fd3aef09?auto=format&fit=crop&q=80&w=1200',
			link: '/productos'
		},
		{
			id: 'servicios',
			title: 'Servicios',
			description: 'Aplicación profesional y certificada en cada proyecto.',
			image:
				'https://images.unsplash.com/photo-1589939705384-5185137a7f0f?auto=format&fit=crop&q=80&w=1200',
			link: '/servicios'
		},
		{
			id: 'sobre-nosotros',
			title: 'Sobre Nosotros',
			description: 'Conoce sobre nuestra misión, visión y compromiso social.',
			image:
				'https://images.unsplash.com/photo-1504307651254-35680f356bfb?auto=format&fit=crop&q=80&w=1200',
			link: '/sobre-nosotros'
		},
		{
			id: 'portafolio',
			title: 'Portafolio',
			description: 'Entra a conocer nuestra trayectoria con demostraciones de trabajos previos.',
			image:
				'https://images.unsplash.com/photo-1503387762-592deb58ef4e?auto=format&fit=crop&q=80&w=1200',
			link: '/contacto'
		},
		{
			id: 'contacto',
			title: 'Contacto',
			description:
				'Comunícate con nosotros por cualquier medio, te brindamos atención personalizada.',
			image:
				'https://images.unsplash.com/photo-1423666639041-f56000c27a9a?auto=format&fit=crop&q=80&w=1200',
			link: '/contacto'
		}
	];
</script>

<svelte:head>
	<title>SC-Servicios | Inicio</title>
</svelte:head>

<section
	class="relative m-0 flex h-[calc(100dvh-5rem)] w-full flex-col justify-center overflow-hidden bg-[#0a1120] p-0"
>
	<div class="relative z-10 mx-auto flex h-full w-full max-w-[1920px] flex-col gap-8">
		<div class="mt-12 h-full w-full px-4 md:px-8">
			<Carousel.Root
				opts={{
					align: 'start',
					dragFree: true,
					loop: true
				}}
				class="group/carousel w-full cursor-grab active:cursor-grabbing"
			>
				<Carousel.Content class="-ml-4 md:-ml-8">
					{#each sections as section}
						<Carousel.Item class="basis-full pl-4 md:basis-1/2 md:pl-8 lg:basis-1/3">
							<a
								href={section.link}
								class="group relative block h-[55vh] max-h-[700px] min-h-[400px] w-full overflow-hidden bg-[#050a14] transition-all duration-500"
							>
								<!-- Image -->
								<img
									src={section.image}
									alt={section.title}
									class="absolute inset-0 h-full w-full scale-100 transform object-cover opacity-60 transition-transform duration-700 ease-in-out group-hover:scale-105 group-hover:opacity-40"
								/>

								<!-- Minimal Overlay Box -->
								<div
									class="absolute inset-10 z-20 flex flex-col items-center justify-center border border-white/20 bg-black/5 text-center backdrop-blur-[2px] transition-colors duration-500 group-hover:border-white/50 group-hover:bg-black/20"
								>
									<h2
										class="mb-4 text-4xl font-bold tracking-tight text-white drop-shadow-lg md:text-5xl"
									>
										{section.title}
									</h2>
									<p class="mx-auto max-w-[85%] text-sm font-light text-white/90 md:text-base">
										{section.description}
									</p>
								</div>
							</a>
						</Carousel.Item>
					{/each}
				</Carousel.Content>

				<!-- Custom Navigation Placed at Bottom Center -->
				<div class="mt-8 flex w-full items-center justify-center gap-6 px-4 text-white md:px-8">
					<Carousel.Previous
						class="static h-10 w-10 translate-y-0 rounded-full border border-white/10 bg-white/5 text-white/70 shadow-none backdrop-blur-sm transition-all hover:bg-white/15 hover:text-white"
					/>
					<span class="text-xs font-light tracking-[0.2em] text-white/50 uppercase">
						desliza hacia los lados
					</span>
					<Carousel.Next
						class="static h-10 w-10 translate-y-0 rounded-full border border-white/10 bg-white/5 text-white/70 shadow-none backdrop-blur-sm transition-all hover:bg-white/15 hover:text-white"
					/>
				</div>
			</Carousel.Root>
		</div>
	</div>
</section>
