<script lang="ts">
	import { page } from '$app/state';
	import Footer from '$lib/footer.svelte';
	import Header from '$lib/header.svelte';
	import gsap from 'gsap';
	import ProjectBlock from './projectBlock.svelte';
	import { finishedProjects } from '$lib/content';

	const id = page.params.id === 'A-C' ? 'A/C' : page.params.id;
	const projects = finishedProjects.filter((project) => project.tags.includes(id));
	let main: gsap.TweenTarget;
	let header: gsap.TweenTarget;

	$effect(() => {
		gsap.from(main, {
			opacity: 0.5,
			y: 200,
			duration: 1,
			ease: 'power1.out'
		});
		gsap.from(header, {
			opacity: 0.5,
			y: 180,
			duration: 1,
			ease: 'power1.out'
		});
	});
</script>

<Header />

<h1
	bind:this={header}
	class=" font-grotesque mx-auto mt-30 mb-14 max-w-7xl px-4 text-6xl font-black md:mt-40 md:mb-20 md:text-7xl lg:text-8xl"
>
	<span class="">{id}</span> Projects
</h1>
<main bind:this={main} class="font-grotesque max-w-9xl mx-auto flex w-full flex-col px-4">
	<section
		class="flex flex-wrap items-center justify-center gap-2 tracking-wide sm:justify-normal md:gap-2 lg:justify-center lg:gap-6"
	>
		{#each projects as project}
			<ProjectBlock {project} />
		{/each}
	</section>
</main>
<Footer />
