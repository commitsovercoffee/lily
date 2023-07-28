<script>
	import { fly } from "svelte/transition";

	let uid = 1;
	let tasks = [];
	let newTask = "";

	function add() {
		tasks = [{ id: uid++, description: newTask }, ...tasks];
		newTask = "";
	}

	function remove(index) {
		tasks.splice(index, 1);
		tasks = tasks;
	}
</script>

<section
	class="my-4 p-4 border-2 border-dashed border-black rounded-xl h-full overflow-scroll"
>
	<input
		bind:value={newTask}
		type="text"
		placeholder="new todo item ..."
		on:keydown={(e) => e.key === "Enter" && add()}
		class="p-4 bg-gray-900 text-gray-50 rounded-xl w-full"
	/>

	<div class="px-4">
		{#each tasks as item, index (item.id)}
			<section
				class="flex my-4 border-b-gray-400 border-b"
				in:fly={{ y: -200, duration: 500 }}
				out:fly={{ x: -200, duration: 500 }}
			>
				<span
					role="button"
					tabindex="0"
					on:keydown={(e) =>
						e.key === "Enter" &&
						remove(index)}
					class="p-2 rounded-full my-auto bg-gray-100 text-xs hover:bg-black hover:text-white delay-50 ease-in duration-200"
					on:click={() => {
						remove(index);
					}}
				>
					&#10005
				</span>
				<p class="m-2 p-2">
					{item.description}
				</p>
			</section>
		{/each}
	</div>
</section>
