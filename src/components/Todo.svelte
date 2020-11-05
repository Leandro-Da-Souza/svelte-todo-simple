<script>
    import { createEventDispatcher } from 'svelte';

    export let todo;

    const dispatch = createEventDispatcher();

    const deletetodo = () => {
        dispatch('deletetodo', todo.id);
    };

    const toggletodo = () => {
        dispatch('toggletodo', todo.id);
    };
</script>

<style>
    .lineThrough {
        text-decoration: line-through;
    }
</style>

<li class="list-group-item d-flex justify-content-between">
    <p class={todo.completed ? 'lineThrough' : ''}>{todo.title}</p>
    <div class="">
        <span class="btn btn-info" on:click={toggletodo}>
            {#if todo.completed}&#9745;{:else}&#9744;{/if}
        </span>
        <span class="btn btn-danger" on:click={deletetodo}>X</span>
    </div>
</li>
