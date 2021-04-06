<script>
	import Day from './components/Day.svelte';
	import Task from './components/Task.svelte';

	import { flip } from 'svelte/animate';

	const flipDurationMs = 300;

	let todos = [
		{ id: 1, done: false, scheduled: false, text: 'write some docs' },
		{ id: 2, done: false, scheduled: false, text: 'start writing JSConf talk' },
		{ id: 3, done: true, scheduled: false, text: 'buy some milk' },
		{ id: 4, done: false, scheduled: false, text: 'mow the lawn' },
		{ id: 5, done: false, scheduled: true, text: 'feed the turtle' },
		{ id: 6, done: false, scheduled: false, text: 'fix some bugs' }
	];

	let schedule = [];

	let uid = todos.length + 1;

	function add(input) {
		const todo = {
			id: uid++,
			done: false,
			scheduled: false,
			text: input.value
		};

		todos = [todo, ...todos];
		input.value = '';
	}

	function remove(todo) {
		todos = todos.filter((t) => t !== todo);
	}
</script>

<main>
	<h1>Chik Chak</h1>
	<input
		class="new-todo"
		placeholder="ugh, what now?"
		on:keydown={(event) => event.key === 'Enter' && add(event.target)}
	/>

	<div class="board">
		<Day />
		<div class="tasklist">
			{#each todos.filter((t) => !t.scheduled) as todo (todo.id)}
				<div animate:flip={{ duration: flipDurationMs }}>
					<svelte:component this={Task} {...todo} />
				</div>
			{/each}
		</div>
	</div>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		margin: 0 auto;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4rem;
		font-weight: 100;
		line-height: 1.1;
		margin: 0 auto;
	}

	.board {
		width: 45em;
		display: flex;
	}

	.new-todo {
		font-size: 1.4em;
		width: 20em;
		margin: 2em 0 1em 0;
		padding: 0.5em;
	}
</style>
