<script lang="ts">
	import { gsap } from 'gsap';
	import { slide } from 'svelte/transition';
	let isHoverSpecialization = $state(0);
	let isHoverProject = $state(0);
	let slideCount = $state(0);
	const incrementSlideCount = () => {
		slideCount++;
		if (slideCount > 2) slideCount = 0;
	};
	function enter(id: number) {
		isHoverSpecialization = id;
	}
	function exist(id: number) {
		isHoverSpecialization = 0;
	}
	function enterProject(id: number) {
		isHoverProject = id;
	}
	function existProject(id: number) {
		isHoverProject = 0;
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
		<p class="text-4xl font-black">MayFair</p>
		<p class="text-sm font-black">Built on Quality. Backed by 40 Years.</p>
	</section>
	<section class="flex gap-10 text-2xl font-extralight">
		<p>About</p>
		<p>Projects</p>
		<p>Contact</p>
	</section>
</header>

<main class="font-grotesque mt-10">
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
		<div class="mt-5">
			<!-- svelte-ignore a11y_no_static_element_interactions -->
			{#each specialize as section}
				<div
					onmouseenter={() => {
						enter(section.id, isHoverSpecialization);
					}}
					onmouseleave={() => {
						exist(section.id, isHoverSpecialization);
					}}
					class="border-primary flex h-[299px] items-center gap-10 border-t-2"
				>
					{#if isHoverSpecialization != section.id}
						<p class="text-5xl">●</p>
						<h3 class="text-7xl font-extralight">{section.header}</h3>
					{:else if isHoverSpecialization === section.id}
						<img src={section.img} alt="MEP services" class="h-full" />

						<div class="flex h-full w-full flex-col justify-between gap-12 pt-5 pr-12 pb-2.5">
							{#if section.id != 1}
								<h4 class="text-4xl font-black">{section.header}</h4>
								<div class="flex flex-col">
									<div class="flex w-[80ch]">
										<p>
											{section.content}
										</p>
									</div>
								</div>
							{:else}
								<h4 class="text-4xl font-black">MEP Services (HVAC, Electrical & Plumbing)</h4>
								<div class="flex flex-col">
									<h5 class="text-3xl font-bold">{section.contentList![slideCount].title}</h5>
									<div class="flex w-[80ch]">
										<p>
											{section.contentList![slideCount].desc}
										</p>
									</div>
									<button class="self-end hover:bg-rose-300" onclick={incrementSlideCount}
										>➜ Next Slide</button
									>
								</div>
							{/if}
						</div>
					{/if}
				</div>
			{/each}
		</div>
	</section>
	<section class="font-grotesque mt-40">
		<div class="mx-auto w-7xl"><h2 class="text-6xl font-black">Our Work</h2></div>
		<div class="mt-5 flex h-[826px] items-center justify-between border-y-2">
			{#each projects as projectSection}
				<!-- svelte-ignore a11y_no_static_element_interactions -->
				<div
					onmouseenter={() => enterProject(projectSection.id)}
					onmouseleave={() => existProject(projectSection.id)}
					class="flex h-full flex-1 items-center justify-center text-5xl font-extralight hover:flex-2"
				>
					{#if isHoverProject == projectSection.id}
						<div class="flex h-full flex-col justify-evenly py-28">
							<p class="text-center">{projectSection.header}</p>
							<p class="text-center text-xl font-light">{projectSection.content}</p>
						</div>
					{:else}
						<p class="text-center">{projectSection.header}</p>
					{/if}
				</div>

				<div class="h-full w-px bg-black"></div>
			{/each}
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
			<p>About</p>
			<p>Projects</p>
			<p>Contact</p>
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
