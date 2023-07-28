<script>
	import Button from "../components/Button.svelte";
	import Tasks from "../components/Tasks.svelte";

	export let title = "A Sassy Title";
	export let content =
		"Lorem ipsum dolor sit amet consectetur adipisicing elit. A, officia dignissimos? Ipsam delectus quaerat asperiores, hic distinctio labore commodi eius impedit voluptatem temporibus maiores, iste nostrum, saepe quis laboriosam tempora!";
	export let src = "./lily.png";

	export let items = [
		{ text: "item1", complete: false },
		{ text: "item2", complete: false },
		{ text: "item3", complete: false },
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
	<p class="p-4 border-2 border-black rounded-xl">
		{content}
	</p>
	<div class="h-96 my-4">
		<Tasks />
	</div>
	<Button label="START" />
</section>
