<script>
	import PromptPage from "./pages/PromptPage.svelte";
	import ReflectPage from "./pages/ReflectPage.svelte";
	import TaskPage from "./pages/TaskPage.svelte";
	import PriorityPage from "./pages/PriorityPage.svelte";
	import RoutinePage from "./pages/RoutinePage.svelte";
	import { page } from "./store.js";
</script>

{#if $page === 1}
	<PromptPage />
{:else if $page === 2}
	<ReflectPage />
{:else if $page === 3}
	<TaskPage />
{:else if $page === 4}
	<PriorityPage />
{:else if $page === 5}
	<RoutinePage />
{/if}
