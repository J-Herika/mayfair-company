<script lang="ts">
	import { tick } from 'svelte';
	import { specialize } from '$lib/content';
	import gsap from 'gsap';

	let slideCount = $state(0);

	let textDiv: gsap.TweenTarget = $state(null);
	let imgDiv: gsap.TweenTarget = $state(null);

	let slideContent: gsap.TweenTarget = $state(null);
	let slideHeader: gsap.TweenTarget = $state(null);

	let headerDot: gsap.TweenTarget = $state(null);
	let headerText: gsap.TweenTarget = $state(null);

	let isHoverSpecialization = $state(false);
	let isHoverSpecial2 = $state(false);
	let isHoverSpecial3 = $state(false);
	let isHoverSpecial4 = $state(false);

	const incrementSlideCount = () => {
		slideCount++;
		if (slideCount > 2) slideCount = 0;
		slideHandler();
	};

	async function slideHandler() {
		await tick();
		gsap.from(slideContent, { opacity: 0, y: -20, duration: 0.4 });
		gsap.from(slideHeader, { opacity: 0, y: -20, duration: 0.4 });
	}

	async function headerHandler() {
		await tick();
		gsap.from(headerDot, { opacity: 0, duration: 0.5, overwrite: false });
		gsap.from(headerText, { opacity: 0, duration: 0.5, overwrite: false });
	}
	async function enterHandler(id: number) {
		switch (id) {
			case 1:
				isHoverSpecialization = true;
				break;
			case 2:
				isHoverSpecial2 = true;
				break;
			case 3:
				isHoverSpecial3 = true;
				break;
			case 4:
				isHoverSpecial4 = true;
				break;

			default:
				break;
		}
		await tick();

		if (textDiv && imgDiv) {
			gsap.fromTo(
				textDiv,
				{ opacity: 0, x: 300, duration: 1, ease: 'power2.out', delay: 0.2 },
				{ opacity: 1, x: 0, duration: 1, overwrite: false, ease: 'power2.out', delay: 0.2 }
			);

			gsap.fromTo(
				imgDiv,
				{ opacity: 0, x: 300, duration: 1, ease: 'power2.out', delay: 0.2 },
				{ opacity: 1, x: 0, duration: 1, overwrite: false, ease: 'power2.out', delay: 0.2 }
			);
		}
	}
	function leaveHandler(id: number) {
		if (textDiv && imgDiv) {
			gsap.to(textDiv, {
				opacity: 0,
				x: -300,
				duration: 0.2,
				ease: 'power2.in',
				onComplete: () => {
					switch (id) {
						case 1:
							isHoverSpecialization = false;
							break;
						case 2:
							isHoverSpecial2 = false;
							break;
						case 3:
							isHoverSpecial3 = false;
							break;
						case 4:
							isHoverSpecial4 = false;
							break;

						default:
							break;
					}
				}
			});
			gsap.to(imgDiv, {
				opacity: 0,
				x: -300,
				duration: 0.2,
				ease: 'power2.in',
				onComplete: () => {
					switch (id) {
						case 1:
							isHoverSpecialization = false;
							break;
						case 2:
							isHoverSpecial2 = false;
							break;
						case 3:
							isHoverSpecial3 = false;
							break;
						case 4:
							isHoverSpecial4 = false;
							break;

						default:
							break;
					}
					headerHandler();
				}
			});
		}
	}
</script>

<section class="font-grotesque mt-20 sm:mt-40 lg:mt-60">
	<div class="mx-auto w-full max-w-7xl">
		<h2 class="text-3xl font-black sm:text-5xl lg:text-6xl">What we Specialize in</h2>
	</div>
	<!-- svelte-ignore a11y_no_static_element_interactions -->
	<div
		onmouseenter={() => enterHandler(specialize[0].id)}
		onmouseleave={() => leaveHandler(specialize[0].id)}
		class="border-primary relative flex min-h-32 flex-col items-start justify-center gap-6 border-t-2 md:flex-row md:items-center md:justify-start lg:h-[299px] lg:items-center lg:justify-start lg:gap-10"
	>
		{#if !isHoverSpecialization}
			<h3
				bind:this={headerText}
				class="spe-header flex items-center gap-6 pl-2 text-3xl font-extralight sm:text-3xl md:gap-10 lg:text-7xl"
			>
				<div class="size-3 rounded-full bg-black"></div>
				<span>{specialize[0].header}</span>
			</h3>
		{:else}
			<img
				bind:this={imgDiv}
				loading="lazy"
				src={specialize[0].img}
				alt="MEP services"
				class="spec-img-div w-full object-cover md:h-full md:w-1/2"
			/>
			<div
				bind:this={textDiv}
				class="flex w-full flex-col justify-between gap-6 pt-4 pr-6 pb-2.5 lg:gap-12"
			>
				<h4 class="text-2xl font-black sm:text-3xl lg:text-4xl">
					MEP Services (HVAC, Electrical & Plumbing)
				</h4>
				<div class="flex flex-col justify-between">
					<h5 bind:this={slideHeader} class="text-xl font-bold sm:text-2xl lg:text-3xl">
						{specialize[0].contentList![slideCount].title}
					</h5>
					<div
						bind:this={slideContent}
						class="flex h-[168px] w-full max-w-prose text-sm font-light lg:h-[96px] lg:text-[16px]"
					>
						<p>
							{specialize[0].contentList![slideCount].desc}
						</p>
					</div>
					<button
						class="mt-2 self-end transition-all duration-250 ease-linear hover:translate-x-2 hover:scale-105 hover:cursor-pointer active:translate-x-2 active:scale-105"
						onclick={incrementSlideCount}
					>
						➜ Next Slide
					</button>
				</div>
			</div>
		{/if}
	</div>
	<!-- svelte-ignore a11y_no_static_element_interactions -->
	<div
		onmouseenter={() => enterHandler(specialize[1].id)}
		onmouseleave={() => leaveHandler(specialize[1].id)}
		class="border-primary relative flex h-auto min-h-33 flex-col items-start justify-center gap-6 border-t-2 md:flex-row md:items-center md:justify-start lg:h-[299px] lg:items-center lg:justify-start lg:gap-10"
	>
		{#if !isHoverSpecial2}
			<h3
				bind:this={headerText}
				class="spe-header flex items-center gap-6 pl-2 text-3xl font-extralight sm:text-3xl md:gap-10 lg:text-7xl"
			>
				<div class="size-3 rounded-full bg-black"></div>
				<span>{specialize[1].header}</span>
			</h3>
		{:else}
			<img
				bind:this={imgDiv}
				loading="lazy"
				src={specialize[1].img}
				alt="MEP services"
				class="spec-img-div w-full object-cover md:h-full md:w-1/2"
			/>
			<div
				bind:this={textDiv}
				class="flex w-full flex-col justify-between gap-6 px-4 py-6 pt-4 pr-6 pb-2.5 md:p-0 lg:gap-12"
			>
				<div class="flex flex-col justify-between">
					<h5 bind:this={slideHeader} class="text-xl font-bold sm:text-2xl lg:text-3xl">
						{specialize[1].header}
					</h5>
					<div
						bind:this={slideContent}
						class="flex h-auto w-full max-w-prose text-sm lg:h-[96px] lg:text-[16px]"
					>
						<p>
							{specialize[1].content}
						</p>
					</div>
				</div>
			</div>
		{/if}
	</div>

	<!-- svelte-ignore a11y_no_static_element_interactions -->
	<div
		onmouseenter={() => enterHandler(specialize[2].id)}
		onmouseleave={() => leaveHandler(specialize[2].id)}
		class="border-primary relative flex h-auto min-h-33 flex-col items-start justify-center gap-6 border-t-2 md:flex-row md:items-center md:justify-start lg:h-[299px] lg:items-center lg:justify-start lg:gap-10"
	>
		{#if !isHoverSpecial3}
			<h3
				bind:this={headerText}
				class="spe-header flex items-center gap-6 pl-2 text-3xl font-extralight sm:text-3xl md:gap-10 lg:text-7xl"
			>
				<div class="size-3 rounded-full bg-black"></div>
				<span>{specialize[2].header}</span>
			</h3>
		{:else}
			<img
				bind:this={imgDiv}
				loading="lazy"
				src={specialize[2].img}
				alt="MEP services"
				class="spec-img-div w-full object-cover md:h-full md:w-1/2"
			/>
			<div
				bind:this={textDiv}
				class="flex w-full flex-col justify-between gap-6 px-4 py-6 pt-4 pr-6 pb-2.5 md:p-0 lg:gap-12"
			>
				<div class="flex flex-col justify-between">
					<h5 bind:this={slideHeader} class="text-xl font-bold sm:text-2xl lg:text-3xl">
						{specialize[2].header}
					</h5>
					<div
						bind:this={slideContent}
						class="flex h-auto w-full max-w-prose text-sm lg:h-[96px] lg:text-[16px]"
					>
						<p>
							{specialize[2].content}
						</p>
					</div>
				</div>
			</div>
		{/if}
	</div>
	<!-- svelte-ignore a11y_no_static_element_interactions -->
	<div
		onmouseenter={() => enterHandler(specialize[3].id)}
		onmouseleave={() => leaveHandler(specialize[3].id)}
		class="border-primary relative flex h-auto min-h-33 flex-col items-start justify-center gap-6 border-y-2 md:flex-row md:items-center md:justify-start lg:h-[299px] lg:items-center lg:justify-start lg:gap-10"
	>
		{#if !isHoverSpecial4}
			<h3
				bind:this={headerText}
				class="spe-header flex items-center gap-6 pl-2 text-3xl font-extralight sm:text-3xl md:gap-10 lg:text-7xl"
			>
				<div class="size-3 rounded-full bg-black"></div>
				<span>{specialize[3].header}</span>
			</h3>
		{:else}
			<img
				bind:this={imgDiv}
				loading="lazy"
				src={specialize[3].img}
				alt="MEP services"
				class="spec-img-div w-full object-cover md:h-full md:w-1/2"
			/>
			<div
				bind:this={textDiv}
				class="flex w-full flex-col justify-between gap-6 px-4 py-6 pt-4 pr-6 pb-2.5 md:p-0 lg:gap-12"
			>
				<div class="flex flex-col justify-between">
					<h5 bind:this={slideHeader} class="text-xl font-bold sm:text-2xl lg:text-3xl">
						{specialize[3].header}
					</h5>
					<div
						bind:this={slideContent}
						class="flex h-[168px] w-full max-w-prose text-sm lg:h-[96px] lg:text-[16px]"
					>
						<p>
							{specialize[3].content}
						</p>
					</div>
				</div>
			</div>
		{/if}
	</div>
</section>
