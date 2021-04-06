<!-- TODO: 
  add an animation into done 
  add a drop shadow while grabbed (other styles?)
-->
<script>
	import { Draggable } from 'svelte-fullcalendar';

	export let done;
	export let text;
	export let id;
	export let scheduled;
</script>

<Draggable eventData={{ title: text, duration: '00:30' }}>
	<div class:done {id} {scheduled}>{text}</div>
</Draggable>

<style>
	div {
		height: 30px;
		width: 220px;
		display: flex;
		align-items: center;
		justify-content: center;
		border: 2px solid #ff3e00;
		border-radius: 5px;
		padding: 2px 20px 4px 20px;
		margin: 10px;
		overflow: hidden;
		transition: background-color 0.2s;
	}

	.done {
		background-color: hsl(15, 100%, 90%);
		text-decoration: line-through wavy #ff3e00;
	}

	.done:hover {
		background-color: hsl(15, 100%, 90%);
	}

	div:hover {
		background-color: hsl(15, 100%, 94%);
	}
</style>
