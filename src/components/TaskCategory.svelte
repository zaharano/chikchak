<!-- TODO: Can I just move all the sortable/draggable shit into the the top level and declare it all there within onMount? -->
<script>
	import Sortable from 'sortablejs';
	import Task from './Task.svelte';
	import { onMount } from 'svelte';
	import { flip } from 'svelte/animate';

	export let id;
	export let title;
	// export let safe;
	// export let color;
	export let todos;

	const flipDurationMs = 300;
	let domId = `cat${id}`;

	onMount(() => {
		Sortable.create(document.getElementById(domId));
	});
</script>

<h2>{title}</h2>
<div id={domId}>
	{#each todos as todo (todo.id)}
		<div animate:flip={{ duration: flipDurationMs }}>
			<svelte:component this={Task} {...todo} />
		</div>
	{/each}
</div>

<style>
	h2 {
		text-align: left;
	}
</style>
