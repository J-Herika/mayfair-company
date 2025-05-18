<script lang="ts">
	import { tick } from 'svelte';
	import { projects } from '$lib/content';
	import gsap from 'gsap';

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
		tick();
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
	<div class="mt-5 flex flex-col overflow-hidden border-y-2 md:flex-row">
		<div
			onmouseenter={() => enterProject(projects[0].id)}
			onmouseleave={() => existProject(projects[0].id)}
			class="flex h-[400px] min-w-[250px] flex-1 items-center justify-center px-4 py-10 text-2xl font-extralight transition-all duration-300 hover:flex-[1.5] md:h-[600px] md:text-5xl"
		>
			{#if isHoverProject}
				<div bind:this={projContentDiv} class="flex h-full flex-col justify-evenly text-center">
					<p>{projects[0].header}</p>
					<p class="mt-4 text-sm font-light md:text-xl">{projects[0].content}</p>
				</div>
			{:else}
				<p bind:this={projheader} class="text-center">{projects[0].header}</p>
			{/if}
		</div>

		<div class="hidden h-full w-px bg-black md:block"></div>

		<div
			onmouseenter={() => enterProject(projects[1].id)}
			onmouseleave={() => existProject(projects[1].id)}
			class="flex h-[400px] min-w-[250px] flex-1 items-center justify-center px-4 py-10 text-2xl font-extralight transition-all duration-300 hover:flex-[1.5] md:h-[600px] md:text-5xl"
		>
			{#if isHoverProject2}
				<div bind:this={projContentDiv} class="flex h-full flex-col justify-evenly text-center">
					<p>{projects[1].header}</p>
					<p class="mt-4 text-sm font-light md:text-xl">{projects[1].content}</p>
				</div>
			{:else}
				<p bind:this={projheader} class="text-center">{projects[1].header}</p>
			{/if}
		</div>

		<div class="hidden h-full w-px bg-black md:block"></div>

		<div
			onmouseenter={() => enterProject(projects[2].id)}
			onmouseleave={() => existProject(projects[2].id)}
			class="flex h-[400px] min-w-[250px] flex-1 items-center justify-center px-4 py-10 text-2xl font-extralight transition-all duration-300 hover:flex-[1.5] md:h-[600px] md:text-5xl"
		>
			{#if isHoverProject3}
				<div bind:this={projContentDiv} class="flex h-full flex-col justify-evenly text-center">
					<p>{projects[2].header}</p>
					<p class="mt-4 text-sm font-light md:text-xl">{projects[2].content}</p>
				</div>
			{:else}
				<p bind:this={projheader} class="text-center">{projects[2].header}</p>
			{/if}
		</div>

		<div class="hidden h-full w-px bg-black md:block"></div>

		<!-- svelte-ignore a11y_no_static_element_interactions -->
		<div
			onmouseenter={() => enterProject(projects[3].id)}
			onmouseleave={() => existProject(projects[3].id)}
			class="flex h-[400px] min-w-[250px] flex-1 items-center justify-center px-4 py-10 text-2xl font-extralight transition-all duration-300 hover:flex-[1.5] md:h-[600px] md:text-5xl"
		>
			{#if isHoverProject4}
				<div bind:this={projContentDiv} class="flex h-full flex-col justify-evenly text-center">
					<p>{projects[3].header}</p>
					<p class="mt-4 text-sm font-light md:text-xl">{projects[3].content}</p>
				</div>
			{:else}
				<p bind:this={projheader} class="text-center">{projects[3].header}</p>
			{/if}
		</div>

		<div class="hidden h-full w-px bg-black md:block"></div>

		<div
			onmouseenter={() => enterProject(projects[4].id)}
			onmouseleave={() => existProject(projects[4].id)}
			class="flex h-[400px] min-w-[250px] flex-1 items-center justify-center px-4 py-10 text-2xl font-extralight transition-all duration-300 hover:flex-[1.5] md:h-[600px] md:text-5xl"
		>
			{#if isHoverProject5}
				<div bind:this={projContentDiv} class="flex h-full flex-col justify-evenly text-center">
					<p>{projects[4].header}</p>
					<p class="mt-4 text-sm font-light md:text-xl">{projects[4].content}</p>
				</div>
			{:else}
				<p bind:this={projheader} class="text-center">{projects[4].header}</p>
			{/if}
		</div>
	</div>
</section>
