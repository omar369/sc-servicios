<script lang="ts">
	import * as NavigationMenu from '$lib/components/ui/navigation-menu/index.js';
	import { slide } from 'svelte/transition';
	import Menu from 'lucide-svelte/icons/menu';
	import Home from 'lucide-svelte/icons/home';
	import X from 'lucide-svelte/icons/x';

	const links = [
		{ href: '/', label: 'Inicio' },
		{ href: '/servicios', label: 'Servicios' },
		{ href: '/productos', label: 'Productos' },
		{ href: '/sobre-nosotros', label: 'Sobre nosotros' },
		{ href: '/contacto', label: 'Contacto' }
	];

	let y = $state(0);
	let lastY = $state(0);
	let hidden = $state(false);
	let menuOpen = $state(false);

	$effect(() => {
		// Hide navbar when scrolling down past 80px, show when scrolling up
		if (y > 80 && y > lastY) {
			hidden = true;
			menuOpen = false; // Close menu on scroll down
		} else if (y < lastY) {
			hidden = false;
		}
		lastY = y;
	});
</script>

<svelte:head>
	<script type="module">
		import { CreateHilosWhatsappButton } from 'https://button.hilos.io/whatsapp-button.esm.js';
		CreateHilosWhatsappButton({
			phone: '+524421878771',
			message: '',
			color: '#ffffff',
			background: '#72d66e',
			position: 'right',
			padding: '20'
		});
	</script>
</svelte:head>

<svelte:window bind:scrollY={y} />

<header
	class="sticky top-0 z-50 w-full border-b bg-[#f28705] shadow-sm transition-transform duration-300 {hidden
		? '-translate-y-full'
		: 'translate-y-0'}"
>
	<div class="relative container mx-auto flex h-20 items-center justify-between px-6 md:px-12">
		<!-- Left section: Hamburger (mobile) + Logo -->
		<div class="flex items-center gap-2 md:gap-4">
			<button
				class="z-10 -ml-2 p-2 text-white transition-transform duration-300 hover:scale-105 active:scale-95 md:hidden"
				onclick={() => (menuOpen = !menuOpen)}
				aria-label="Abrir Menú"
			>
				{#if menuOpen}
					<X class="h-6 w-6" />
				{:else}
					<Home class="h-6 w-6" />
				{/if}
			</button>

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

		<!-- Desktop CTAs -->
		<div class="flex hidden items-center gap-4 md:flex">
			<a
				href="https://api.whatsapp.com/send?phone=524421878771&text=Bienvenido%20a%20SC%20Servicios"
				target="_blank"
				rel="noopener noreferrer"
				class="flex h-10 w-10 items-center justify-center rounded-full border-2 border-white bg-[#25D366] text-white transition-all hover:bg-[#20ba5a] hover:shadow-lg active:scale-95"
				aria-label="WhatsApp"
			>
				<img src="/wa_logo.svg" alt="WhatsApp Icon" class="h-12 w-12 object-contain" />
			</a>
		</div>

		<script type="module">
			import { CreateHilosWhatsappButton } from 'https://button.hilos.io/whatsapp-button.esm.js';
			CreateHilosWhatsappButton({
				phone: '+524421878771',
				message: '',
				color: '#ffffff',
				background: '#72d66e',
				position: 'right',
				padding: '20'
			});
		</script>
		<!-- Mobile Whatsapp -->
		<div class="flex md:hidden">
			<a
				href="https://api.whatsapp.com/send?phone=524421878771&text=Bienvenido%20a%20SC%20Servicios"
				target="_blank"
				rel="noopener noreferrer"
				class="flex h-10 w-10 items-center justify-center rounded-full border border-white bg-[#25D366] text-white transition-all active:scale-95"
				aria-label="WhatsApp"
			>
				<img src="/wa_logo.svg" alt="WhatsApp Icon" class="h-8 w-8 object-contain" />
			</a>
		</div>
	</div>

	<!-- Mobile Menu Dropdown -->
	{#if menuOpen}
		<div
			class="absolute top-[80px] left-0 w-full border-t border-white/20 bg-[#f28705] shadow-lg md:hidden"
			transition:slide={{ duration: 300 }}
		>
			<nav class="flex flex-col items-center space-y-6 py-6">
				{#each links as link}
					<a
						href={link.href}
						class="text-xl font-medium text-white transition-colors hover:text-gray-200"
						onclick={() => (menuOpen = false)}
					>
						{link.label}
					</a>
				{/each}
			</nav>
		</div>
	{/if}
</header>
