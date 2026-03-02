<script lang="ts">
	let isSetupComplete = $state(false); // Toggle this to test both setups
</script>

<div
	class="relative transform overflow-hidden rounded-2xl border border-white/20 bg-white/10 p-8 shadow-2xl backdrop-blur-2xl transition-all duration-500 dark:border-white/10 dark:bg-black/20"
>
	<!-- Reflection overlay -->
	<div
		class="pointer-events-none absolute inset-0 rounded-2xl bg-gradient-to-tr from-white/5 to-transparent"
	></div>

	<div class="relative z-10">
		<div class="mb-8 text-center">
			<div
				class="mx-auto mb-4 flex h-16 w-16 items-center justify-center rounded-2xl border border-white/20 bg-gradient-to-br from-blue-500 to-indigo-600 shadow-lg"
			>
				<svg
					xmlns="http://www.w3.org/2000/svg"
					fill="none"
					viewBox="0 0 24 24"
					stroke-width="1.5"
					stroke="currentColor"
					class="h-8 w-8 text-white"
				>
					<path
						stroke-linecap="round"
						stroke-linejoin="round"
						d="M16.5 10.5V6.75a4.5 4.5 0 1 0-9 0v3.75m-.75 11.25h10.5a2.25 2.25 0 0 0 2.25-2.25v-6.75a2.25 2.25 0 0 0-2.25-2.25H6.75a2.25 2.25 0 0 0-2.25 2.25v6.75a2.25 2.25 0 0 0 2.25 2.25Z"
					/>
				</svg>
			</div>
			<h1 class="text-2xl font-semibold tracking-tight text-white">Vault</h1>
			<p class="mt-1 text-sm text-slate-300">
				{#if !isSetupComplete}
					Create your secure local vault
				{:else}
					Enter master password to unlock
				{/if}
			</p>
		</div>

		{#if !isSetupComplete}
			<!-- Setup Mode -->
			<form
				class="space-y-4"
				onsubmit={(e) => {
					e.preventDefault();
					isSetupComplete = true;
				}}
			>
				<div>
					<label for="name" class="mb-1 ml-1 block text-sm font-medium text-slate-200">Name</label>
					<input
						type="text"
						id="name"
						placeholder="Jane Doe"
						required
						class="w-full rounded-xl border border-white/10 bg-black/20 px-4 py-3 text-white placeholder-slate-400 shadow-inner transition-shadow duration-200 focus:border-transparent focus:ring-2 focus:ring-blue-500 focus:outline-none"
					/>
				</div>
				<div>
					<label for="master-password" class="mb-1 ml-1 block text-sm font-medium text-slate-200"
						>Master Password</label
					>
					<input
						type="password"
						id="master-password"
						placeholder="••••••••••••"
						required
						class="w-full rounded-xl border border-white/10 bg-black/20 px-4 py-3 text-white placeholder-slate-400 shadow-inner transition-shadow duration-200 focus:border-transparent focus:ring-2 focus:ring-blue-500 focus:outline-none"
					/>
					<p class="mt-2 ml-1 text-xs text-slate-400">
						Ensure this is strong. It cannot be recovered.
					</p>
				</div>

				<button
					type="submit"
					class="mt-6 flex w-full items-center justify-center gap-2 rounded-xl bg-blue-500 px-4 py-3 font-medium text-white shadow-lg shadow-blue-500/30 transition-colors duration-200 hover:bg-blue-400 active:bg-blue-600"
				>
					Create Vault
					<svg
						xmlns="http://www.w3.org/2000/svg"
						fill="none"
						viewBox="0 0 24 24"
						stroke-width="2"
						stroke="currentColor"
						class="h-4 w-4"
					>
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							d="M13.5 4.5 21 12m0 0-7.5 7.5M21 12H3"
						/>
					</svg>
				</button>
			</form>
		{:else}
			<!-- Unlock Mode -->
			<form
				class="space-y-4"
				onsubmit={(e) => {
					e.preventDefault();
					console.log('Unlock attempted');
				}}
			>
				<div class="mb-6 text-center">
					<div
						class="mb-2 inline-block rounded-full border border-white/5 bg-white/10 p-1 px-3 backdrop-blur-md"
					>
						<span class="text-xs font-medium text-slate-300">Welcome back, Jane</span>
					</div>
				</div>

				<div>
					<label for="unlock-password" class="sr-only">Master Password</label>
					<input
						type="password"
						id="unlock-password"
						placeholder="Master Password"
						required
						class="w-full rounded-xl border border-white/10 bg-black/20 px-4 py-3 text-center tracking-widest text-white placeholder-slate-400 shadow-inner transition-shadow duration-200 focus:border-transparent focus:ring-2 focus:ring-blue-500 focus:outline-none"
					/>
				</div>

				<button
					type="submit"
					class="flex w-full items-center justify-center gap-2 rounded-xl border border-white/10 bg-white/20 px-4 py-3 font-medium text-white backdrop-blur-md transition-colors duration-200 hover:bg-white/30 active:bg-white/10"
				>
					Unlock
					<svg
						xmlns="http://www.w3.org/2000/svg"
						fill="none"
						viewBox="0 0 24 24"
						stroke-width="2"
						stroke="currentColor"
						class="h-4 w-4"
					>
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							d="M13.5 4.5 21 12m0 0-7.5 7.5M21 12H3"
						/>
					</svg>
				</button>
			</form>

			<div class="mt-8 border-t border-white/10 pt-4 text-center">
				<p
					class="flex items-center justify-center gap-1 text-[10px] tracking-wide text-slate-400 uppercase"
				>
					<svg
						xmlns="http://www.w3.org/2000/svg"
						fill="none"
						viewBox="0 0 24 24"
						stroke-width="2"
						stroke="currentColor"
						class="h-3 w-3"
					>
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							d="M16.5 10.5V6.75a4.5 4.5 0 1 0-9 0v3.75m-.75 11.25h10.5a2.25 2.25 0 0 0 2.25-2.25v-6.75a2.25 2.25 0 0 0-2.25-2.25H6.75a2.25 2.25 0 0 0-2.25 2.25v6.75a2.25 2.25 0 0 0 2.25 2.25Z"
						/>
					</svg>
					Session locks after 5m entirely locally
				</p>
			</div>
		{/if}
	</div>
</div>

<!-- Only for development/demo purposes to allow easy toggling -->
<button
	onclick={() => (isSetupComplete = !isSetupComplete)}
	class="absolute bottom-4 left-1/2 mx-auto mt-8 flex -translate-x-1/2 rounded-full border border-white/5 bg-white/5 px-3 py-1 text-xs text-white/50 transition-colors hover:bg-white/10"
>
	Toggle View (Demo)
</button>
