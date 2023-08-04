<script>
	import Button from "../components/Button.svelte";
	import Draggable from "../components/Draggable.svelte";

	export let title = "Routine";
	export let content =
		"Lorem ipsum dolor sit amet consectetur adipisicing elit.";
	export let src = "./lily.png";
</script>

<section class="flex justify-center">
	<div class="p-2 m-4">
		<section class="w-screen p-6">
			<h2 class="p-4 text-4xl font-bold">
				{title}
			</h2>
			<p class="p-4">
				{content}
			</p>
			<section class="p-2 my-8 h-32 border-2 rounded-xl" />
			<Draggable>drink ample water</Draggable>
		</section>

		<Button label="START" />
		<Button label="START" />
	</div>
</section>
