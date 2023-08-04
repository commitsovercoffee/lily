<script>
	let left = 420;
	let top = 220;

	const cardStyle =
		"cursor-move select-none p-8 bg-red-300 h-8 w-16 ease-linear absolute";
	const canMove = " absolute";
	const dayRowStyle =
		"py-8 px-2 bg-teal-100 w-full border-b-2 border-black ";
	const dayLabelStyle =
		"py-8 px-2 w-32  border-b-2 border-r-2 border-black  ";

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
			childRect.top >= parentRect.top &&
			childRect.top <= parentRect.bottom &&
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
		} else if (isAlmostInside(wed, card)) {
			snapVertically(wed, card);
		} else if (isAlmostInside(thurs, card)) {
			snapVertically(thurs, card);
		} else if (isAlmostInside(fri, card)) {
			snapVertically(fri, card);
		} else if (isAlmostInside(sat, card)) {
			snapVertically(sat, card);
		} else if (isAlmostInside(sun, card)) {
			snapVertically(sun, card);
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
	class="p-2 absolute z-10 bg-red-100 cursor-move select-none rounded-xl"
>
	Drink a glass of water.
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

<div class="flex">
	<p class={dayLabelStyle}>Monday</p>
	<section bind:this={mon} class={dayRowStyle} />
</div>

<div class="flex">
	<p class={dayLabelStyle}>Tuesday</p>
	<section bind:this={tue} class={dayRowStyle} />
</div>

<div class="flex">
	<p class={dayLabelStyle}>Wednesday</p>
	<section bind:this={wed} class={dayRowStyle} />
</div>
<div class="flex">
	<p class={dayLabelStyle}>Thursday</p>
	<section bind:this={thurs} class={dayRowStyle} />
</div>
<div class="flex">
	<p class={dayLabelStyle}>Friday</p>
	<section bind:this={fri} class={dayRowStyle} />
</div>
<div class="flex">
	<p class={dayLabelStyle}>Saturday</p>
	<section bind:this={sat} class={dayRowStyle} />
</div>
<div class="flex">
	<p class={dayLabelStyle}>Sunday</p>
	<section bind:this={sun} class={dayRowStyle} />
</div>
