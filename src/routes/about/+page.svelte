<script lang="ts">
	import Footer from '$lib/footer.svelte';
	import Header from '$lib/header.svelte';
	import gsap from 'gsap';

	let main: gsap.TweenTarget;

  $effect(() => {
		gsap.from(main, {
			opacity: 0.5,
			y: 200,
			duration: 1,
			ease: 'power1.out'
		});
	});
</script>

<Header />
<main
	bind:this={main}
	class="font-grotesque mx-auto mt-30 flex w-full max-w-4xl flex-col gap-14 px-4 md:mt-40 md:gap-20"
>
	<h1 class="text-6xl font-black md:text-7xl lg:text-8xl">About us</h1>
	<div
		class="text-primary font-montserrat flex max-w-[80ch] flex-col gap-6 font-normal tracking-wide md:text-lg"
	>
		<p>
			We are currently executing major contracts across the UAE. Our scope includes design and
			execution for a wide range of applications—luxury villas, commercial and residential
			buildings, hospitals, and more.
		</p>
		<p>
			In addition to turnkey projects, we also undertake maintenance contracts with both private
			clients and government bodies such as the P.W.D. and D.S.S.C.B. We place special emphasis on
			the quality and responsiveness of our maintenance services.
		</p>
		<p>
			MayFair Co., is approved by most government departments and currently executes prestigious
			projects—including school developments for the P.W.D. Our work consistently meets the highest
			standards of client, contractor, and consultant satisfaction.
		</p>
		<p>
			Our reputation is built on exceptional workmanship, strict adherence to deadlines, strong
			project management, and uncompromising quality control—making us a trusted partner across
			sectors.
		</p>
	</div>
</main>
<Footer />
