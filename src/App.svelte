<script lang="ts">
	import ModeSwitcher from './ModeSwitcher.svelte';
	import Tailwindcss from './Tailwindcss.svelte';
	import Timer from './Timer.svelte';
	const params = new URL(window.location.toString()).searchParams;
	let title = params.get('title') ?? 'Game Time';
	let target = params.get('time') ?? '0';
	const ts = parseInt(target, 10) * 1000;
</script>
<Tailwindcss />
<ModeSwitcher />
<main class="p-4 mx-auto text-center max-w-xl">
	<h1 class="uppercase text-6xl leading-normal font-thin text-svelte">{title}</h1>
	<div class="text-2xl mt-12 font-bold">
		<Timer endDate={ts}/>
	</div>
</main>