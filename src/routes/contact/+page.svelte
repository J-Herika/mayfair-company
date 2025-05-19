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
	class="font-grotesque mx-auto mt-30 flex w-full max-w-4xl flex-col gap-20 px-4 md:mt-40 md:gap-20"
>
	<h1 class="text-6xl font-black md:text-7xl lg:text-8xl">Contact</h1>
	<div
		class="text-primary flex flex-col gap-15 font-normal tracking-wide md:text-lg lg:flex-row-reverse lg:justify-between"
	>
		<section
			class="flex flex-col gap-15 md:flex-row-reverse sm:justify-end md:gap-30 lg:justify-between lg:gap-0 sm:px-2 md:p-0 lg:flex-col"
		>
			<div>
				<h2 class="mb-4 text-3xl font-black md:text-4xl">Contact Info</h2>
				<div class="font-montserrat flex items-center gap-2">
					<p class="font-montserrat text-xl font-medium">Phone:</p>
					<p class="font-montserrat text-lg font-light">(+971) - 507670657</p>
				</div>
				<div class="font-montserrat flex items-center gap-2">
					<p class="font-montserrat text-xl font-medium">Email:</p>
					<p class="font-montserrat text-lg font-light">Mayfair.ybc@gmail.com</p>
				</div>
			</div>
			<div>
				<h2 class="mb-4 text-3xl font-black md:text-4xl">Working Hours</h2>
				<div class="flex flex-col gap-1">
					<div class="font-montserrat flex max-w-md items-center justify-between gap-2">
						<p class="font-montserrat text-xl font-medium">Weekdays:</p>
						<p class="font-montserrat text-lg font-light">8:00am to 5:00am</p>
					</div>
					<div class="font-montserrat flex max-w-md items-center justify-between gap-2">
						<p class="font-montserrat text-xl font-medium">Friday:</p>
						<p class="font-montserrat text-lg font-light">8:00am to 5:00am</p>
					</div>
					<div class="font-montserrat flex max-w-md items-center justify-between gap-2">
						<p class="font-montserrat text-xl font-medium">Saturday:</p>
						<p class="font-montserrat text-lg font-light">8:00am to 5:00am</p>
					</div>
					<div class="font-montserrat flex max-w-md items-center justify-between gap-2">
						<p class="font-montserrat text-xl font-medium">Sunday:</p>
						<p class="font-montserrat text-lg font-light">CLOSED</p>
					</div>
				</div>
			</div>
		</section>
		<section class="h-full min-h-60 w-full max-w-xl">
			<h2 class="mb-4 text-3xl font-black lg:hidden">Visit us</h2>

			<!-- svelte-ignore a11y_missing_attribute -->
			<iframe
				src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d26404.528263964785!2d55.37142251333319!3d25.129185087361947!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x3e5f6443320894a9%3A0xded8f3eee9ea9f99!2sA.S.B%20Tower!5e1!3m2!1sen!2str!4v1747680861411!5m2!1sen!2str"
				width="100%"
				height="400"
				style="border:0;"
				loading="lazy"
				referrerpolicy="no-referrer-when-downgrade"
			></iframe>
		</section>
	</div>
</main>
<Footer />
