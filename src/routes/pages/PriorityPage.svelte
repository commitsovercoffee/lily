<script>
	import Button from "../components/Button.svelte";

	export let title = "Time to Choose";
	export let content =
		"Lorem ipsum dolor sit amet consectetur adipisicing elit. A, officia dignissimos? Ipsam delectus quaerat asperiores, hic distinctio labore commodi eius impedit voluptatem temporibus maiores, iste nostrum, saepe quis laboriosam tempora!";
	export let src = "./lily.png";

	let add = [
		"stay hydrated.",
		"plan a romantic date.",
		"increase work hours.",
	];
</script>

<section class="mx-auto p-2 my-16 w-4/12">
	<div class="p-2 m-4 flex justify-evenly place-self-center">
		<img
			class="object-cover h-60 w-auto"
			{src}
			alt="sketch of lily."
		/>
		<section class="w-96">
			<h2 class="p-4 text-4xl font-bold">
				{title}
			</h2>
			<p class="p-4">
				{content}
			</p>
		</section>
	</div>

	<div class="p-2 m-4 flex">
		<section
			class="basis-1/2 m-4 p-4 border-2 border-dashed border-black rounded-xl overflow-scroll"
		>
			<h1 class="p-2 text-xl rounded-xl bg-black text-white">
				+ Add
			</h1>
			<ul class="">
				{#each add as items}
					<li class="p-2 my-2">
						<input type="checkbox" />
						{items}
					</li>
				{/each}
			</ul>
		</section>
		<section
			class="basis-1/2 m-4 p-4 border-2 border-dashed border-black rounded-xl overflow-scroll"
		>
			<h1 class="p-2 text-xl rounded-xl bg-black text-white">
				- Subtract
			</h1>
			<ul class="">
				{#each add as items}
					<li class="p-2 my-2">
						{items}
					</li>
				{/each}
			</ul>
		</section>
	</div>
	<Button label="START" />
</section>
