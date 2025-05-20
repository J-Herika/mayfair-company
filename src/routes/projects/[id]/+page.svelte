<script lang="ts">
	import { page } from '$app/state';
	import Footer from '$lib/footer.svelte';
	import Header from '$lib/header.svelte';
	import gsap from 'gsap';
	import ProjectBlock from './projectBlock.svelte';

	const id = page.params.id;

	let main: gsap.TweenTarget;

	// $effect(() => {
	// 	gsap.from(main, {
	// 		opacity: 0.5,
	// 		y: 200,
	// 		duration: 1,
	// 		ease: 'power1.out'
	// 	});
	// });
</script>

<Header />
<!-- bind:this={main} -->
<div class="mx-auto max-w-4xl px-4">
	<h1
		class="font-grotesque mt-30 mb-14 text-6xl font-black md:mt-40 md:mb-20 md:text-7xl lg:text-8xl"
	>
		Projects
	</h1>
</div>

<main class="font-grotesque mx-auto flex w-full max-w-7xl flex-col px-4">
	<section
		class="flex flex-wrap items-center gap-2 tracking-wide md:justify-normal md:gap-2 lg:gap-6"
	>
		<ProjectBlock />
		<ProjectBlock />
		<ProjectBlock />
		<ProjectBlock />
	</section>
</main>
<Footer />
