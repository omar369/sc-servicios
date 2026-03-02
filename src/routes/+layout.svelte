<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/favicon.svg';
	import Navbar from '$lib/components/Navbar.svelte';

	let { children } = $props();
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>

<div class="relative flex min-h-screen flex-col bg-background font-sans antialiased text-foreground">
	<Navbar />
	<main class="flex-1">
		{@render children()}
	</main>
</div>
