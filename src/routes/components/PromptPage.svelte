<script>
	import Button from "./Button.svelte";

	export let title = "A Sassy Title";
	export let content =
		"Lorem ipsum dolor sit amet consectetur adipisicing elit. A, officia dignissimos? Ipsam delectus quaerat asperiores, hic distinctio labore commodi eius impedit voluptatem temporibus maiores, iste nostrum, saepe quis laboriosam tempora!";
	export let src = "./lily.png";
</script>

<section class="h-screen flex justify-center">
	<div class="p-2 m-4 flex flex-wrap place-self-center">
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
			<Button label="START" />
		</section>
	</div>
</section>
