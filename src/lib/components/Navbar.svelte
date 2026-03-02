<script lang="ts">
	import * as NavigationMenu from '$lib/components/ui/navigation-menu/index.js';
	import { buttonVariants } from '$lib/components/ui/button/index.js';

	import Home from 'lucide-svelte/icons/home';

	const links = [
		{ href: '/', label: 'Inicio' },
		{ href: '/servicios', label: 'Servicios' },
		{ href: '/productos', label: 'Productos' },
		{ href: '/sobre-nosotros', label: 'Sobre nosotros' },
		{ href: '/contacto', label: 'Contacto' }
	];
</script>

<header
	class="full bg-bag-secondary bckground/80 bg-secondaryund sticky border-b shadow-sm backdrop-blur-md transition-all duration-300 supports-[backdrop-filter]:bg-background/60"
>
	<div
		class="relative container mx-auto flex h-20 items-center justify-between bg-[#f28705] px-6 md:px-12"
	>
		<!-- Logo -->
		<div class="flex items-center gap-2 md:gap-4">
			<a
				href="/"
				class="z-10 transition-transform duration-300 hover:scale-105"
				aria-label="Inicio"
			>
				<Home class="h-6 w-6 text-white" />
			</a>
			<a
				href="/"
				class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 transition-transform duration-300 hover:scale-105 md:static md:translate-x-0 md:translate-y-0"
				aria-label="Logo"
			>
				<img src="/sc_logo.svg" alt="Logo" class="h-12 w-auto" />
			</a>
		</div>

		<!-- Desktop Nav -->
		<NavigationMenu.Root class="hidden md:flex">
			<NavigationMenu.List class="flex space-x-1 lg:space-x-4">
				{#each links as link}
					<NavigationMenu.Item>
						<NavigationMenu.Link
							href={link.href}
							class="group white relative inline-flex h-10 w-max items-center justify-center rounded-md bg-transparent px-4 py-2 text-base font-medium text-white transition-colors hover:text-primary focus:text-primary focus:outline-none disabled:pointer-events-none disabled:opacity-50"
						>
							{link.label}
							<!-- Subline animation on hover -->
							<span
								class="absolute bottom-0 left-0 h-0.5 w-0 bg-white transition-all duration-300 group-hover:w-full"
							></span>
						</NavigationMenu.Link>
					</NavigationMenu.Item>
				{/each}
			</NavigationMenu.List>
		</NavigationMenu.Root>

		<!-- CTAs -->
		<div class="flex items-center gap-4">
			<a
				href="https://wa.me/your-number"
				target="_blank"
				rel="noopener noreferrer"
				class="flex h-10 w-10 items-center justify-center rounded-full border-2 border-white bg-[#25D366] text-white transition-all hover:bg-[#20ba5a] hover:shadow-lg active:scale-95"
				aria-label="WhatsApp"
			>
				<img src="/wa_logo.svg" alt="WhatsApp Icon" class="h-12 w-12 object-contain" />
			</a>
		</div>
	</div>
</header>
