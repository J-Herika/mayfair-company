<script lang="ts">
	let props = $props();
</script>

<!-- svelte-ignore a11y_no_static_element_interactions -->
<div
	onmouseenter={() => props.enterProject(props.project.id)}
	onmouseleave={() => props.existProject(props.project.id)}
	class="flex h-[400px] min-w-[250px] flex-1 items-center justify-center border-1 border-black px-4 py-10 text-2xl font-extralight transition-all duration-250 hover:flex-[1.5] active:flex-[1.5] md:h-[600px] md:text-5xl"
>
	{#if props.isHover}
		<div class="flex h-full max-w-xl flex-col items-center justify-evenly text-center">
			<p>{props.project.header}</p>
			<p class="mt-4 text-sm font-light md:text-xl">{props.project.content}</p>
			<a
				href={props.link}
				class="border-primary text-primary hover:bg-primary active:bg-primary active:text-background hover:text-background mt-10 w-1/2 border-4 px-6 py-2 text-base transition-all duration-300 ease-linear hover:cursor-pointer sm:mt-12 sm:px-6 sm:py-5 sm:text-lg"
			>
				<button>Projects</button>
			</a>
		</div>
	{:else}
		<p class="text-center">{props.project.header}</p>
	{/if}
</div>
