<script>
	import Button from "../components/Button.svelte";

	export let title = "A Sassy Title";
	export let content =
		"Lorem ipsum dolor sit amet consectetur adipisicing elit. A, officia dignissimos? Ipsam delectus quaerat asperiores, hic distinctio labore commodi eius impedit voluptatem temporibus maiores, iste nostrum, saepe quis laboriosam tempora!";
	export let src = "./lily.png";

	export let items = [
		{ text: "item1", complete: false },
		{ text: "item2", complete: false },
		{ text: "item3", complete: false },
	];

	let notes = "";
</script>

<section class="h-screen flex justify-center">
	<section class="p-2 my-4 place-self-center w-96">
		<h2 class="p-4 text-4xl font-bold">
			{title}
		</h2>
		<p class="p-4">
			{content}
		</p>
		<ul class="p-4 my-4 list-disc list-inside pointer w-min">
			{#each items as item}
				<li
					class={item.complete
						? "line-through cursor-pointer"
						: "cursor-pointer"}
					on:click={() => {
						item.complete = !item.complete;
					}}
				>
					{item.text}
				</li>
			{/each}
		</ul>
		<Button label="START" />
	</section>

	<textarea
		bind:value={notes}
		placeholder="Start writing here ..."
		class="p-4 m-4 text-xl text-gray-600 place-self-center rounded-2xl border-2 border-black border-dashed w-4/12 h-96"
	/>
</section>
