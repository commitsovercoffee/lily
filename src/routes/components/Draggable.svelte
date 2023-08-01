<script>
	export let left = 100;
	export let top = 100;

	// vars binded to elements
	let container;
	let card;

	let containerRect;
	let cardRect;

	let offsetX = 0;
	let offsetY = 0;
	let isDragging = false;

	function onMouseDown(e) {
		isDragging = true;
		offsetX = e.clientX - left;
		offsetY = e.clientY - top;
	}

	function checkOverlap(e) {}

	function onMouseMove(e) {
		containerRect = container.getBoundingClientRect();
		cardRect = card.getBoundingClientRect();

		if (isDragging) {
			left = e.clientX - offsetX;
			top = e.clientY - offsetY;

			console.log(checkOverlap(e));

			// Check if cardRect is inside containerRect
			const isCardInsideContainer =
				cardRect.left >= containerRect.left &&
				cardRect.top >= containerRect.top &&
				cardRect.right <= containerRect.right &&
				cardRect.bottom <= containerRect.bottom;

			console.log(
				"Is card inside container?",
				isCardInsideContainer
			);

			// write code to snap card vertical center of container
			if (isCardInsideContainer) {
				const containerCenterY =
					containerRect.top +
					containerRect.height / 2;
				const cardCenterY =
					cardRect.top + cardRect.height / 2;
				const offsetYCenter =
					containerCenterY - cardCenterY;
				top += offsetYCenter;
			}
		}
	}

	function onMouseUp() {
		isDragging = false;
	}
</script>

<section bind:this={container} class="bg-sky-100 w-96 h-16" />
<section
	bind:this={card}
	on:mousedown={onMouseDown}
	style="left: {left}px; top: {top}px;"
	class="cursor-move select-none bg-red-300 absolute h-8 w-16 transition-transform ease-linear"
>
	<slot />
</section>

<svelte:window on:mouseup={onMouseUp} on:mousemove={onMouseMove} />
