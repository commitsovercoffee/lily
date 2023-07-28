<script>
	import PromptPage from "./components/PromptPage.svelte";
	import ReflectPage from "./components/ReflectPage.svelte";
	import { page } from "./store.js";
</script>

{#if $page === 1}
	<PromptPage />
{:else if $page === 2}
	<ReflectPage />
{/if}
