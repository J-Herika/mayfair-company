<script lang="ts">
	import { gsap } from 'gsap';
	import { onMount, tick } from 'svelte';
	import { slide } from 'svelte/transition';

	let textDiv: gsap.TweenTarget = $state(null);
	let imgDiv: gsap.TweenTarget = $state(null);

	let slideContent: gsap.TweenTarget = $state(null);
	let slideHeader: gsap.TweenTarget = $state(null);

	let headerDot: gsap.TweenTarget = $state(null);
	let headerText: gsap.TweenTarget = $state(null);

	let isHoverSpecialization = $state(false);
	let isHoverProject = $state(false);
	let slideCount = $state(0);

	let isHoverSpecial2 = $state(false);
	let isHoverSpecial3 = $state(false);
	let isHoverSpecial4 = $state(false);

	let isHoverProject2 = $state(false);
	let isHoverProject3 = $state(false);
	let isHoverProject4 = $state(false);
	let isHoverProject5 = $state(false);

	let projContentDiv: gsap.TweenTarget = $state(null);
	let projheader: gsap.TweenTarget = $state(null);

	const incrementSlideCount = () => {
		slideCount++;
		if (slideCount > 2) slideCount = 0;
		slideHandler();
	};

	async function slideHandler() {
		await tick();
		gsap.from(slideContent, { opacity: 0, y: -20, duration: 1 });
		gsap.from(slideHeader, { opacity: 0, y: -20, duration: 1 });
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
				{ opacity: 0, x: 300, duration: 1, ease: 'power2.out' },
				{ opacity: 1, x: 0, duration: 1, overwrite: false, ease: 'power2.out' }
			);

			gsap.fromTo(
				imgDiv,
				{ opacity: 0, x: 300, duration: 1, ease: 'power2.out' },
				{ opacity: 1, x: 0, duration: 1, overwrite: false, ease: 'power2.out' }
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
			{ opacity: 0, duration: 1, y: 200, ease: 'power2.out' },
			{ opacity: 1, duration: 1, y: 0, ease: 'power2.out' }
		);
	}
	async function existProject(id: number) {
		gsap.to(projContentDiv, {
			opacity: 0,
			duration: 0.2,
			ease: 'circ.in'
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
					case 4:
						isHoverProject5 = false;
						break;

					default:
						break;
				}
				console.log('done');
			}
		});
	}

	const mepInfo = [
		{
			title: 'Electrical',
			desc: 'We handle complete electrical systems from design to execution—including high- and low-voltage switchgears, substation installations (11kV & 33kV), fire alarm systems, CCTV, intercoms, and backup generators. Maintenance services cover villas, multi-story buildings, hotels, and institutional facilities.'
		},
		{
			title: 'HVAC (Air Conditioning)',
			desc: 'We design, install, and maintain advanced air conditioning systems, including chillers, cooling towers, AHUs, VAVs, BMS, ductwork, and chilled water systems. Our projects span commercial, residential, and critical infrastructure like hospitals and printing presses.'
		},
		{
			title: 'Plumbing',
			desc: 'We offer complete water supply, drainage, and fire-fighting system installations. Services include sanitary ware, solar and electric water heaters, central filtration systems, booster pumps, and all hot/cold piping. Our team also manages long-term maintenance across sectors like education, hospitality, and healthcare.'
		}
	];

	const specialize = [
		{
			id: 1,
			header: 'MEP Services ( HVAC, Electrical & Plumbing )',
			img: '/mepImg.webp',
			contentList: [
				{
					title: 'Electrical',
					desc: 'We handle complete electrical systems from design to execution—including high- and low-voltage switchgears, substation installations (11kV & 33kV), fire alarm systems, CCTV, intercoms, and backup generators. Maintenance services cover villas, multi-story buildings, hotels, and institutional facilities.'
				},
				{
					title: 'HVAC (Air Conditioning)',
					desc: 'We design, install, and maintain advanced air conditioning systems, including chillers, cooling towers, AHUs, VAVs, BMS, ductwork, and chilled water systems. Our projects span commercial, residential, and critical infrastructure like hospitals and printing presses.'
				},
				{
					title: 'Plumbing',
					desc: 'We offer complete water supply, drainage, and fire-fighting system installations. Services include sanitary ware, solar and electric water heaters, central filtration systems, booster pumps, and all hot/cold piping. Our team also manages long-term maintenance across sectors like education, hospitality, and healthcare.'
				}
			]
		},
		{
			id: 2,
			header: 'Civil Works',
			img: '/civil.webp',
			content:
				'With decades of experience in structural construction, we deliver complete civil contracting solutions from design to project handover. Our team is equipped with the expertise and equipment to execute complex builds with high-quality workmanship and time-bound delivery. We work across sectors including residential, commercial, educational, and institutional developments.'
		},
		{
			id: 3,
			header: 'Pneumatic Tube Systems',
			img: '/pts.webp',
			content:
				'We are specialists in the design, supply, installation, testing, commissioning, and maintenance of Pneumatic Tube Systems—especially in healthcare environments. From transfer stations to blowers and accessories, our systems are engineered for speed, reliability, and hygiene. Trusted by hospitals across the region, our PTS solutions enhance medical logistics and operational efficiency.'
		},
		{
			id: 4,
			header: 'Maintenance Services',
			img: '/maintenance.webp',
			content:
				'We offer professional maintenance across electrical, HVAC, and plumbing systems for villas, multi-story buildings, hospitals, mosques, schools, and hotels. Our electrical work covers switchgears, MATV systems, music systems, and diesel generators. HVAC services include central air conditioning systems in residential and commercial facilities. Plumbing maintenance covers drainage, water supply, and fire-fighting systems, handled by qualified engineers and experienced technicians. We serve both private clients and government departments with reliable, responsive service.'
		}
	];

	const projects = [
		{
			id: 1,
			header: 'civil',
			content:
				'Our civil works include residential, commercial, and institutional buildings—managed from design to completion with a focus on quality, safety, and structural durability.'
		},
		{
			id: 2,
			header: 'Decoration',
			content:
				'We deliver interior and exterior decoration projects with attention to detail, combining aesthetics and technical precision across villas, offices, and public spaces.'
		},
		{
			id: 3,
			header: 'Pneumatic Tube System',
			content:
				'We design and install Pneumatic Tube Systems for hospitals, ensuring efficient, hygienic transport systems that meet critical healthcare standards.'
		},
		{
			id: 4,
			header: 'A/C',
			content:
				'Our air conditioning projects cover design, installation, and maintenance of central systems—chillers, AHUs, ductwork, and more—for all building types.'
		},
		{
			id: 5,
			header: 'MEP',
			content:
				'We execute integrated mechanical, electrical, and plumbing works—delivering reliable, coordinated systems for residential, commercial, and institutional projects.'
		}
	];
</script>

<header class="font-grotesque mx-auto mt-5 flex w-7xl items-center justify-between">
	<section>
		<p
			class="relative inline-block text-4xl font-black after:absolute after:right-0 after:bottom-0 after:h-0 after:w-full after:bg-[#1E1E1E50] after:px-1 after:transition-all after:duration-300 hover:after:h-1/2"
		>
			<a href="/">MayFair</a>
		</p>
		<p class="text-sm font-black">Built on Quality. Backed by 40 Years.</p>
	</section>
	<section class="flex gap-10 text-2xl font-extralight">
		<a
			href="/"
			class="relative inline-block after:absolute after:right-0 after:bottom-0 after:h-0 after:w-full after:bg-[#1E1E1E50] after:px-1 after:transition-all after:duration-300 hover:after:h-1/2"
			>About</a
		><a
			href="/"
			class="relative inline-block after:absolute after:right-0 after:bottom-0 after:h-0 after:w-full after:bg-[#1E1E1E50] after:px-1 after:transition-all after:duration-300 hover:after:h-1/2"
			>Projects</a
		><a
			href="/"
			class="relative inline-block after:absolute after:right-0 after:bottom-0 after:h-0 after:w-full after:bg-[#1E1E1E50] after:px-1 after:transition-all after:duration-300 hover:after:h-1/2"
			>Contact</a
		>
	</section>
</header>

<main class="font-grotesque mt-10 overflow-x-hidden">
	<div class="mx-auto w-7xl">
		<img src="/Hero-Img.webp" alt="A black building designed like a Jenga" />
		<section class="mt-10">
			<h1 class="text-8xl font-black">MayFair Group</h1>
			<div class="max-w-[80ch]">
				<p class="mt-2.5 text-2xl font-light">
					Established in 1984, we bring 40 years of proven expertise in civil works, MEP systems,
					and critical infrastructure—built to perform, built to last.
				</p>
			</div>
		</section>
	</div>
	<section class="font-grotesque mt-60">
		<div class="mx-auto w-7xl"><h2 class="text-6xl font-black">What we Specialize in</h2></div>

		<!-- svelte-ignore a11y_no_static_element_interactions -->
		<div
			onmouseenter={() => {
				enterHandler(specialize[0].id);
			}}
			onmouseleave={() => {
				leaveHandler(specialize[0].id);
			}}
			class="border-primary relative flex h-[299px] items-center gap-10 border-t-2"
		>
			{#if !isHoverSpecialization}
				<p bind:this={headerDot} class="text-5xl">●</p>
				<h3 bind:this={headerText} class="spe-header text-7xl font-extralight">
					{specialize[0].header}
				</h3>
			{:else}
				<img
					bind:this={imgDiv}
					src={specialize[0].img}
					alt="MEP services"
					class="spec-img-div h-full"
				/>
				<div bind:this={textDiv} class=" flex flex-col justify-between gap-12 pt-5 pr-12 pb-2.5">
					<h4 class="text-4xl font-black">MEP Services (HVAC, Electrical & Plumbing)</h4>
					<div class="flex flex-col">
						<h5 bind:this={slideHeader} class="text-3xl font-bold">
							{specialize[0].contentList![slideCount].title}
						</h5>
						<div bind:this={slideContent} class="flex w-[80ch]">
							<p>
								{specialize[0].contentList![slideCount].desc}
							</p>
						</div>
						<button
							class="self-end transition-all duration-250 ease-linear hover:translate-x-2 hover:scale-105 hover:cursor-pointer"
							onclick={incrementSlideCount}>➜ Next Slide</button
						>
					</div>
				</div>
			{/if}
		</div>
		<!-- svelte-ignore a11y_no_static_element_interactions -->
		<div
			onmouseenter={() => {
				enterHandler(specialize[1].id);
			}}
			onmouseleave={() => {
				leaveHandler(specialize[1].id);
			}}
			class="border-primary relative flex h-[299px] items-center gap-10 border-t-2"
		>
			{#if !isHoverSpecial2}
				<p bind:this={headerDot} class="text-5xl">●</p>
				<h3 bind:this={headerText} class="spe-header text-7xl font-extralight">
					{specialize[1].header}
				</h3>
			{:else}
				<img
					bind:this={imgDiv}
					src={specialize[1].img}
					alt="MEP services"
					class="spec-img-div h-full"
				/>
				<div bind:this={textDiv} class=" flex flex-col justify-between gap-12 pt-5 pr-12 pb-2.5">
					<h4 class="text-4xl font-black">{specialize[1].header}</h4>

					<div bind:this={slideContent} class="flex w-[80ch]">
						<p>
							{specialize[1].content}
						</p>
					</div>
				</div>
			{/if}
		</div>
		<!-- svelte-ignore a11y_no_static_element_interactions -->
		<div
			onmouseenter={() => {
				enterHandler(specialize[2].id);
			}}
			onmouseleave={() => {
				leaveHandler(specialize[2].id);
			}}
			class="border-primary relative flex h-[299px] items-center gap-10 border-t-2"
		>
			{#if !isHoverSpecial3}
				<p bind:this={headerDot} class="text-5xl">●</p>
				<h3 bind:this={headerText} class="spe-header text-7xl font-extralight">
					{specialize[2].header}
				</h3>
			{:else}
				<img
					bind:this={imgDiv}
					src={specialize[2].img}
					alt="MEP services"
					class="spec-img-div h-full"
				/>
				<div bind:this={textDiv} class=" flex flex-col justify-between gap-12 pt-5 pr-12 pb-2.5">
					<h4 class="text-4xl font-black">{specialize[2].header}</h4>

					<div bind:this={slideContent} class="flex w-[80ch]">
						<p>
							{specialize[2].content}
						</p>
					</div>
				</div>
			{/if}
		</div>
		<!-- svelte-ignore a11y_no_static_element_interactions -->
		<div
			onmouseenter={() => {
				enterHandler(specialize[3].id);
			}}
			onmouseleave={() => {
				leaveHandler(specialize[3].id);
			}}
			class="border-primary relative flex h-[299px] items-center gap-10 border-t-2"
		>
			{#if !isHoverSpecial4}
				<p bind:this={headerDot} class="text-5xl">●</p>
				<h3 bind:this={headerText} class="spe-header text-7xl font-extralight">
					{specialize[3].header}
				</h3>
			{:else}
				<img
					bind:this={imgDiv}
					src={specialize[3].img}
					alt="MEP services"
					class="spec-img-div h-full"
				/>
				<div bind:this={textDiv} class=" flex flex-col justify-between gap-12 pt-5 pr-12 pb-2.5">
					<h4 class="text-4xl font-black">{specialize[3].header}</h4>

					<div bind:this={slideContent} class="flex w-[80ch]">
						<p>
							{specialize[3].content}
						</p>
					</div>
				</div>
			{/if}
		</div>
	</section>
	<section class="font-grotesque mt-40">
		<div class="mx-auto w-7xl"><h2 class="text-6xl font-black">Our Work</h2></div>
		<div class="mt-5 flex h-[826px] items-center justify-between border-y-2">
			<!-- svelte-ignore a11y_no_static_element_interactions -->
			<div
				onmouseenter={() => {
					enterProject(projects[0].id);
				}}
				onmouseleave={() => {
					existProject(projects[0].id);
				}}
				class="flex h-full flex-1 items-center justify-center text-5xl font-extralight transition-all duration-250 hover:flex-2"
			>
				{#if isHoverProject}
					<div bind:this={projContentDiv} class="flex h-full flex-col justify-evenly py-28">
						<p class="text-center">{projects[0].header}</p>
						<p class="text-center text-xl font-light">{projects[0].content}</p>
					</div>
				{:else}
					<p bind:this={projheader} class="text-center">{projects[0].header}</p>
				{/if}
			</div>

			<div class="h-full w-px bg-black"></div>
			<!-- svelte-ignore a11y_no_static_element_interactions -->
			<div
				onmouseenter={() => {
					enterProject(projects[1].id);
				}}
				onmouseleave={() => {
					existProject(projects[1].id);
				}}
				class="flex h-full flex-1 items-center justify-center text-5xl font-extralight transition-all duration-250 hover:flex-2"
			>
				{#if isHoverProject2}
					<div bind:this={projContentDiv} class="flex h-full flex-col justify-evenly py-28">
						<p class="text-center">{projects[1].header}</p>
						<p class="text-center text-xl font-light">{projects[1].content}</p>
					</div>
				{:else}
					<p bind:this={projheader} class="text-center">{projects[1].header}</p>
				{/if}
			</div>

			<!-- svelte-ignore a11y_no_static_element_interactions -->
			<div class="h-full w-px bg-black"></div>
			<!-- svelte-ignore a11y_no_static_element_interactions -->
			<div
				onmouseenter={() => {
					enterProject(projects[2].id);
				}}
				onmouseleave={() => {
					existProject(projects[2].id);
				}}
				class="flex h-full flex-1 items-center justify-center text-5xl font-extralight transition-all duration-250 hover:flex-2"
			>
				{#if isHoverProject3}
					<div bind:this={projContentDiv} class="flex h-full flex-col justify-evenly py-28">
						<p class="text-center">{projects[2].header}</p>
						<p class="text-center text-xl font-light">{projects[2].content}</p>
					</div>
				{:else}
					<p bind:this={projheader} class="text-center">{projects[2].header}</p>
				{/if}
			</div>

			<div class="h-full w-px bg-black"></div>
			<!-- svelte-ignore a11y_no_static_element_interactions -->
			<div
				onmouseenter={() => {
					enterProject(projects[3].id);
				}}
				onmouseleave={() => {
					existProject(projects[3].id);
				}}
				class="flex h-full flex-1 items-center justify-center text-5xl font-extralight transition-all duration-250 hover:flex-2"
			>
				{#if isHoverProject4}
					<div bind:this={projContentDiv} class="flex h-full flex-col justify-evenly py-28">
						<p class="text-center">{projects[3].header}</p>
						<p class="text-center text-xl font-light">{projects[3].content}</p>
					</div>
				{:else}
					<p bind:this={projheader} class="text-center">{projects[3].header}</p>
				{/if}
			</div>

			<div class="h-full w-px bg-black"></div>

			<!-- svelte-ignore a11y_no_static_element_interactions -->
			<div
				onmouseenter={() => {
					enterProject(projects[4].id);
				}}
				onmouseleave={() => {
					existProject(projects[4].id);
				}}
				class="flex h-full flex-1 items-center justify-center text-5xl font-extralight transition-all duration-250 hover:flex-2"
			>
				{#if isHoverProject5}
					<div bind:this={projContentDiv} class="flex h-full flex-col justify-evenly py-28">
						<p class="text-center">{projects[4].header}</p>
						<p class="text-center text-xl font-light text-black">{projects[4].content}</p>
					</div>
				{:else}
					<p bind:this={projheader} class="text-center">{projects[4].header}</p>
				{/if}
			</div>

			<div class="h-full w-px bg-black"></div>
		</div>
	</section>
	<section class="font-grotesque mx-auto mt-40 w-7xl">
		<h2 class="text-6xl font-black">About Us</h2>
		<div class="max-w-[80ch]">
			<p class=" font-montserrat mt-6 text-xl font-normal">
				Mayfair Building Contracting, established in 1984, is a recognized leader in the
				Electro-Mechanical field—specializing in Civil Construction, MEP services, and Pneumatic
				Tube Systems. Backed by a highly experienced team of engineers, supervisors, and
				technicians, we are equipped to meet diverse client requirements and can rapidly mobilize
				resources to any project site.
			</p>
		</div>
		<button class="text-primary mt-12 border-4 px-6 py-5">Read More</button>
	</section>
</main>
<footer class="bg-footer font-grotesque mt-40">
	<div class=" mx-auto flex w-7xl items-center justify-between py-10">
		<section class="w-[24ch]">
			<p class="text-4xl font-black">MayFair</p>
			<p class="text-2xl font-extralight">Legacy Built on Quality, Since 1984.</p>
		</section>
		<section class="flex gap-10 text-2xl font-extralight">
			<a
				href="/"
				class="relative inline-block after:absolute after:right-0 after:bottom-0 after:h-0 after:w-full after:bg-[#1E1E1E50] after:px-1 after:transition-all after:duration-300 hover:after:h-1/2"
				>About</a
			><a
				href="/"
				class="relative inline-block after:absolute after:right-0 after:bottom-0 after:h-0 after:w-full after:bg-[#1E1E1E50] after:px-1 after:transition-all after:duration-300 hover:after:h-1/2"
				>Projects</a
			><a
				href="/"
				class="relative inline-block after:absolute after:right-0 after:bottom-0 after:h-0 after:w-full after:bg-[#1E1E1E50] after:px-1 after:transition-all after:duration-300 hover:after:h-1/2"
				>Contact</a
			>
		</section>
		<section class="flex flex-col gap-3.5">
			<p class="text-3xl font-black">Contact</p>
			<p class="text-xl font-black">
				Number :
				<span class="font-montserrat text-lg font-light">(+971) - 507670657</span>
			</p>

			<iframe
				src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d331.8415044230076!2d-88.53732798262237!3d30.443398996175063!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x889bebc27560cf7d%3A0xda9c6e63fccb006a!2s4405%20Neese%20Ln%2C%20Moss%20Point%2C%20MS%2039563%2C%20USA!5e1!3m2!1sen!2str!4v1747248192466!5m2!1sen!2str"
				width="300"
				height="260"
				style="border:0;"
				allowfullscreen={null}
				loading="lazy"
				referrerpolicy="no-referrer-when-downgrade"
			></iframe>
		</section>
	</div>
	<p class="font-montserrat pt-4 pb-2.5 text-center text-sm font-extralight">
		© 2025 Mayfair Building Contracting LLC. All rights reserved.
	</p>
</footer>
