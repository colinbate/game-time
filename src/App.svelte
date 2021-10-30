<script lang="ts">
	import ModeSwitcher from './ModeSwitcher.svelte';
	import Tailwindcss from './Tailwindcss.svelte';
	import Timer from './Timer.svelte';
	const params = new URL(window.location.toString()).searchParams;
	let title = params.get('title') ?? 'Game Time';
	let target = params.get('time') ?? '0';
	const ts = parseInt(target, 10) * 1000;
	const targetDate = new Date(ts);
	const targetStr = targetDate.toLocaleString();
</script>
<Tailwindcss />
<ModeSwitcher />
<main class="p-4 mx-auto text-center max-w-xl">
	<h1 class="uppercase text-6xl leading-normal font-thin text-svelte">{title}</h1>
	<div class="text-3xl mt-12 font-bold flex flex-col gap-4">
		<Timer endDate={ts}/>
		<div class="text-2xl">until</div>
		<div>{targetStr}</div>
	</div>
</main>