<script lang="ts">
	import { tick } from 'svelte';
	import { projects } from '$lib/content';
	import gsap from 'gsap';
	import Project from './project.svelte';

	let isHoverProject = $state(false);
	let isHoverProject2 = $state(false);
	let isHoverProject3 = $state(false);
	let isHoverProject4 = $state(false);
	let isHoverProject5 = $state(false);

	let projContentDiv: gsap.TweenTarget = $state(null);
	let projheader: gsap.TweenTarget = $state(null);

	async function enterProject(id: number) {
		switch (id) {
			case 1:
				isHoverProject = true;
				break;
			case 2:
				isHoverProject2 = true;
				break;
			case 3:
				isHoverProject3 = true;
				break;
			case 4:
				isHoverProject4 = true;
				break;
			case 5:
				isHoverProject5 = true;
				break;

			default:
				break;
		}

		await tick();
		gsap.fromTo(
			projContentDiv,
			{ opacity: 0, duration: 1, y: 100, ease: 'power2.out' },
			{ opacity: 1, duration: 1, y: 0, ease: 'power2.out' }
		);
	}
	async function existProject(id: number) {
		await tick();
		gsap.to(projContentDiv, {
			opacity: 0,
			duration: 0.2,
			ease: 'expo.in',
			y: 100,
			fontSize: 14
		});
		gsap.to(projheader, {
			opacity: 1,
			duration: 0.2,
			ease: 'power2.in',
			onComplete: () => {
				switch (id) {
					case 1:
						isHoverProject = false;
						break;
					case 2:
						isHoverProject2 = false;
						break;
					case 3:
						isHoverProject3 = false;
						break;
					case 4:
						isHoverProject4 = false;
						break;
					case 5:
						isHoverProject5 = false;
						break;

					default:
						break;
				}
			}
		});
	}
</script>

<section class="font-grotesque mt-40">
	<div class="mx-auto w-full max-w-7xl">
		<h2 class="text-4xl font-black sm:text-5xl md:text-6xl">Our Work</h2>
	</div>

	<!-- svelte-ignore a11y_no_static_element_interactions -->
	<!-- svelte-ignore a11y_no_static_element_interactions -->
	<div class="mt-5 flex flex-col overflow-hidden border-y-2 xl:flex-row">
		<Project
			{enterProject}
			{existProject}
			project={projects[0]}
			isHover={isHoverProject}
			{projContentDiv}
			{projheader}
		/>
		<Project
			{enterProject}
			{existProject}
			project={projects[1]}
			isHover={isHoverProject2}
			{projContentDiv}
			{projheader}
		/>
		<Project
			{enterProject}
			{existProject}
			project={projects[2]}
			isHover={isHoverProject3}
			{projContentDiv}
			{projheader}
		/>
		<Project
			{enterProject}
			{existProject}
			project={projects[3]}
			isHover={isHoverProject4}
			{projContentDiv}
			{projheader}
		/>
		<Project
			{enterProject}
			{existProject}
			project={projects[4]}
			isHover={isHoverProject5}
			{projContentDiv}
			{projheader}
		/>
	</div>
</section>
