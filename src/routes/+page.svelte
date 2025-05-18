<script lang="ts">
	import Specialization from './Specialization.svelte';
	import Footer from '$lib/footer.svelte';
	import Header from '$lib/header.svelte';
	import AboutSection from './aboutSection.svelte';
	import ProjectsSection from './projectsSection.svelte';
	import HeroSection from './heroSection.svelte';
	import gsap from 'gsap';

	let mainSec: gsap.TweenTarget;
	$effect(() => {
		gsap.from(mainSec, {
			opacity: 0.5,
			y: 100,
			duration: 1,
			ease: 'power1.out'
		});
	});
</script>

<Header />

<main bind:this={mainSec} class="font-grotesque mt-10 overflow-x-hidden">
	<HeroSection />
	<Specialization />
	<ProjectsSection />
	<AboutSection />
</main>
<Footer />
