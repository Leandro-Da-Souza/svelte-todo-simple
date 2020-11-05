<script>
    import { createEventDispatcher } from 'svelte';

    import Todo from './Todo.svelte';
    export let todos;

    const dispatch = createEventDispatcher();

    const deletetodo = (e) => {
        dispatch('deletetodo', e.detail);
    };

    const toggletodo = (e) => {
        dispatch('toggletodo', e.detail);
    };
</script>

<ul class="list-group list-group-flush">
    {#each todos as todo}
        <Todo {todo} on:deletetodo={deletetodo} on:toggletodo={toggletodo} />
    {/each}
</ul>
