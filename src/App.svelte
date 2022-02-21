<script lang="ts">
	import TodoItem from './components/TodoItem.svelte';
	import { ITodoItem } from './models';

	let todos: ITodoItem[] = [
		{
			id: new Date().getTime(),
			name: 'Buy laptop',
			createdAt: new Date(),
			done: false
		},
		{
			id: new Date().getTime() - 87273,
			name: 'Play Forza Horizon 4',
			createdAt: new Date(new Date().getTime() - 87273),
			done: false
		}
	];

	const addTodo = (): void => {
		const createdAt = new Date()
		todos = [...todos, { id: createdAt.getTime(), name: 'Input name...', createdAt, done: false }];
	}

</script>
<div>
	{#each todos as todo}
		<TodoItem {todo} on:toggleTodo={() => todo.done = !todo.done} />
	{/each}

	<div>
		<button on:click={addTodo}>
			Add todo
		</button>
	</div>
</div>
