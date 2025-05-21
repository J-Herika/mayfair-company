<script lang="ts">
	const props = $props();
</script>

<div
	class="font-montserrat text-background text-md flex h-[332px] w-[25ch] flex-col justify-between gap-5 rounded-2xl bg-[#1C1C1C] px-3 py-5 font-normal shadow shadow-neutral-700 transition-all duration-250 ease-linear hover:bg-[#1c1c1cef] hover:shadow-lg active:bg-[#1c1c1cef] active:shadow-lg md:w-[30ch] lg:p-5"
>
	<h3 class="font-grotesque text-center text-xl font-black">{props.project.name}</h3>

	<div class="space-y-2">
		<p class="text-lg font-bold">{props.project.description}</p>

		<div class="flex flex-wrap gap-2">
			<p class="font-medium">Consultant:</p>
			{#if props.project.consultants}
				<p class="opacity-70">{props.project.consultants}</p>
			{:else}
				<p class="opacity-70">Client</p>
			{/if}
		</div>

		<div class="flex flex-wrap gap-2">
			<p class="font-medium">Value:</p>
			<p class="opacity-70">{props.project.contractValue}</p>
		</div>
	</div>

	<h4 class="font-grotesque place-self-center font-black">
		{props.project.tags.join(' & ')}
	</h4>
</div>
