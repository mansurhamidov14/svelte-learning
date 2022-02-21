<script lang="ts">
    import { createEventDispatcher } from 'svelte';
    import { ITodoItem } from '../models';

    const dispatch = createEventDispatcher();

    export let todo: ITodoItem;

    const handleTodoClick = (): void => {
        dispatch('toggleTodo')
    }
</script>

<div class="todo-item">
    <h3 contenteditable="true" bind:innerHTML={todo.name} class="todo-item__title"></h3>
    <div class="todo-item__description">{todo.createdAt.toLocaleDateString()}</div>
    <button class="todo-item__toggle" on:click={handleTodoClick} class:done={todo.done}>{todo.done ? 'Done!' : 'Not done'}</button>
</div>

<style>
    .todo-item {
        border: 2px solid grey;
        padding: 12px;
        margin: 12px;
    }
    .todo-item__title {
        margin: 0;
    }
    .todo-item__description {
        color: #676767;
    }
    .todo-item__toggle {
        cursor: pointer;
        border: none;
        border-radius: 5px;
        padding: 8px 14px;
        color: white;
        background-color: rgb(214, 55, 55);
        margin-top: 12px;
    }
    .todo-item__toggle:focus {
        background-color: rgb(214, 55, 55);
    }
    .todo-item__toggle.done {
        background-color: rgb(13, 146, 13);
    }
</style>