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

	const projectTags: string[] = [
		'Civil',
		'MEP',
		'Electrical',
		'Plumbing',
		'A-C',
		'Pneumatic Tube System',
		'Decoration'
	];

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
	}
	async function existProject(id: number) {
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
</script>

<section class="font-grotesque mt-40 scroll-mt-47" id="projects">
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
			link={`/projects/${projectTags[0]}`}
		/>
		<Project
			{enterProject}
			{existProject}
			project={projects[1]}
			isHover={isHoverProject2}
			link={`/projects/${projectTags[6]}`}
		/>
		<Project
			{enterProject}
			{existProject}
			project={projects[2]}
			isHover={isHoverProject3}
			link={`/projects/${projectTags[5]}`}
		/>
		<Project
			{enterProject}
			{existProject}
			project={projects[3]}
			isHover={isHoverProject4}
			link={`/projects/${projectTags[4]}`}
		/>
		<Project
			{enterProject}
			{existProject}
			project={projects[4]}
			isHover={isHoverProject5}
			link={`/projects/${projectTags[1]}`}
		/>
	</div>
</section>
