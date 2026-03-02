<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<!-- Setup system fonts for Apple-like look -->
	<style>
		:root {
			font-family:
				-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif,
				'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol';
		}
	</style>
</svelte:head>

<div
	class="relative flex min-h-screen w-full items-center justify-center overflow-hidden bg-slate-900 text-slate-100"
>
	<!-- macOS-style Abstract Gradient Background -->
	<div class="absolute inset-0 z-0">
		<div
			class="absolute top-[-10%] left-[-10%] h-[50%] w-[50%] animate-pulse rounded-full bg-blue-600 opacity-70 mix-blend-screen blur-[120px] filter"
			style="animation-duration: 10s;"
		></div>
		<div
			class="absolute right-[-10%] bottom-[-10%] h-[60%] w-[60%] animate-pulse rounded-full bg-teal-500 opacity-60 mix-blend-screen blur-[120px] filter"
			style="animation-duration: 8s; animation-delay: 2s;"
		></div>
		<div
			class="absolute top-[20%] right-[10%] h-[40%] w-[40%] animate-pulse rounded-full bg-indigo-500 opacity-50 mix-blend-screen blur-[100px] filter"
			style="animation-duration: 12s; animation-delay: 1s;"
		></div>
	</div>

	<!-- Main Content Area (Glassmorphic Window) -->
	<main class="relative z-10 w-full max-w-md p-6">
		{@render children()}
	</main>
</div>
