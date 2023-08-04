<script>
	let left = 100;
	let top = 100;

	const cardStyle =
		"cursor-move select-none p-8 bg-red-300 h-8 w-16 ease-linear absolute";
	const canMove = " absolute";

	let mon;
	let tue;
	let wed;
	let thurs;
	let fri;
	let sat;
	let sun;
	let card;

	let offsetX = 0;
	let offsetY = 0;

	let isDragging = false;
	let isInside = false;

	function isAlmostInside(parent, child) {
		const parentRect = parent.getBoundingClientRect();
		const childRect = child.getBoundingClientRect();

		let isInside =
			// top
			childRect.top >= parentRect.top - childRect.height &&
			childRect.top <= parentRect.bottom + childRect.height &&
			// left
			childRect.left >= parentRect.left - childRect.width &&
			childRect.left <= parentRect.right + childRect.width &&
			// right
			childRect.right <= parentRect.right + childRect.width &&
			childRect.right >= parentRect.left - childRect.width;

		return isInside;
	}

	function snapVertically(parent, child) {
		const parentRect = parent.getBoundingClientRect();
		const childRect = child.getBoundingClientRect();

		// write code to snap card vertical center of container
		const parentCenterY = parentRect.top + parentRect.height / 2;
		const childCenterY = childRect.top + childRect.height / 2;

		top += parentCenterY - childCenterY;
	}

	function onMouseUp() {
		isDragging = false;
		isInside = false;

		if (isAlmostInside(mon, card)) {
			snapVertically(mon, card);
		} else if (isAlmostInside(tue, card)) {
			snapVertically(tue, card);
		}
	}
</script>

<!-- This is card -->
<section
	bind:this={card}
	on:mousedown={(e) => {
		isDragging = true;
		offsetX = e.clientX - left;
		offsetY = e.clientY - top;
	}}
	style="left: {left}px; top: {top}px;"
	class="absolute z-10 bg-red-100 cursor-move select-none"
>
	Sample
</section>

<svelte:window
	on:mouseup={onMouseUp}
	on:mousemove={(e) => {
		if (isDragging) {
			left = e.clientX - offsetX;
			top = e.clientY - offsetY;
		}
	}}
/>

<section bind:this={mon} class="relative m-16 p-16 bg-teal-100 w-full h-8" />
<section bind:this={tue} class="relative m-16 p-16 bg-sky-100 w-full h-8" />
<section bind:this={wed} class="relative m-16 p-16 bg-sky-100 w-full h-8" />
<section bind:this={thurs} class="relative m-16 p-16 bg-sky-100 w-full h-8" />
<section bind:this={fri} class="relative m-16 p-16 bg-sky-100 w-full h-8" />
<section bind:this={sat} class="relative m-16 p-16 bg-sky-100 w-full h-8" />
<section bind:this={sun} class="relative m-16 p-16 bg-sky-100 w-full h-8" />
