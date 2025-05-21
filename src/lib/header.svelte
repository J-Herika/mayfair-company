<script lang="ts">
	import gsap from 'gsap';
	import { tick } from 'svelte';
	let headerSec: gsap.TweenTarget;
	$effect(() => {
		gsap.from(headerSec, {
			opacity: 0.5,
			y: -50,
			duration: 1,
			ease: 'power1.out'
		});
	});

	function leavePageHandler() {
		gsap.from(headerSec, {
			opacity: 0.5,
			y: -50,
			duration: 1,
			ease: 'power1.out',
			rotateX: 120
		});
	}
</script>

<header bind:this={headerSec} class="font-grotesque mx-auto mt-5 w-full max-w-7xl px-4">
	<div class="flex flex-col gap-4 md:flex-row md:items-center md:justify-between">
		<section>
			<p
				class="relative inline-block text-3xl font-black after:absolute after:right-0 after:bottom-0 after:h-0 after:w-full after:bg-[#1E1E1E50] after:px-1 after:transition-all after:duration-300 hover:after:h-1/2 active:after:h-1/2 md:text-4xl"
			>
				<a href="/" onclick={leavePageHandler}>MayFair</a>
			</p>
			<p class="text-xs font-black md:text-sm">Built on Quality. Backed by 40 Years.</p>
		</section>

		<section class="flex gap-2 text-lg font-extralight md:gap-10 md:text-2xl">
			<a
				href="/about"
				class="relative inline-block after:absolute after:right-0 after:bottom-0 after:h-0 after:w-full after:bg-[#1E1E1E50] after:px-1 after:transition-all after:duration-300 hover:after:h-1/2 active:after:h-1/2"
				>About</a
			>
			<a
				href={'/#projects'}
				class="relative inline-block after:absolute after:right-0 after:bottom-0 after:h-0 after:w-full after:bg-[#1E1E1E50] after:px-1 after:transition-all after:duration-300 hover:after:h-1/2 active:after:h-1/2"
				>Projects</a
			>
			<a
				href="/contact"
				class="relative inline-block after:absolute after:right-0 after:bottom-0 after:h-0 after:w-full after:bg-[#1E1E1E50] after:px-1 after:transition-all after:duration-300 hover:after:h-1/2 active:after:h-1/2"
				>Contact</a
			>
		</section>
	</div>
</header>
