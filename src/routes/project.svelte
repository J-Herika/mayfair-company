<script lang="ts">
	import { tick } from 'svelte';
	import gsap from 'gsap';

	let props = $props();
</script>

<!-- svelte-ignore a11y_no_static_element_interactions -->
<div
	onmouseenter={() => props.enterProject(props.project.id)}
	onmouseleave={() => props.existProject(props.project.id)}
	class="flex h-[400px] min-w-[250px] flex-1 items-center justify-center px-4 py-10 text-2xl font-extralight transition-all duration-300 hover:flex-[1.5] active:flex-[1.5] md:h-[600px] md:text-5xl"
>
	{#if props.isHover}
		<div class="flex h-full max-w-xl flex-col justify-evenly text-center">
			<p>{props.project.header}</p>
			<p class="mt-4 text-sm font-light md:text-xl">{props.project.content}</p>
		</div>
	{:else}
		<p class="text-center">{props.project.header}</p>
	{/if}
</div>

<div class="hidden h-full w-px bg-black md:block"></div>
