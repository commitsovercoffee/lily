<script>
	export let left = 100;
	export let top = 100;

	const cardStyle =
		"cursor-move select-none p-8 bg-red-300 h-8 w-16 ease-linear absolute";

	let isCardInsideContainer = false;
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
		}
	}

	function onMouseUp() {
		isDragging = false;

		// Check if cardRect is inside containerRect
		isCardInsideContainer =
			// top
			cardRect.top >= containerRect.top - cardRect.height &&
			cardRect.top <=
				containerRect.bottom + cardRect.height &&
			// left
			cardRect.left >= containerRect.left - cardRect.width &&
			cardRect.left <= containerRect.right + cardRect.width &&
			// right

			cardRect.right <=
				containerRect.right + cardRect.width &&
			cardRect.right >= containerRect.left - cardRect.width;

		console.log("Is card inside container?", isCardInsideContainer);

		// write code to snap card vertical center of container
		if (isCardInsideContainer) {
			const containerCenterY =
				containerRect.top + containerRect.height / 2;
			const cardCenterY = cardRect.top + cardRect.height / 2;

			const offsetYCenter = containerCenterY - cardCenterY;

			top += offsetYCenter;
		}
	}
</script>

<section bind:this={container} class="relative m-16 p-16 bg-sky-100 w-96 h-8" />

<!-- This is card -->
<section
	bind:this={card}
	on:mousedown={onMouseDown}
	style="left: {left}px; top: {top}px;"
	class={isCardInsideContainer ? cardStyle : cardStyle}
>
	<slot />
</section>

<svelte:window on:mouseup={onMouseUp} on:mousemove={onMouseMove} />
