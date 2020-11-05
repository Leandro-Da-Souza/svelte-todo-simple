<script>
    import { createEventDispatcher } from 'svelte';

    let title = '';
    const dispatch = createEventDispatcher();

    const onSubmit = (e) => {
        e.preventDefault();
        let newTodo = {
            id: Math.floor(Math.random() * 1000),
            title: title,
            completed: false,
        };

        dispatch('addtodo', newTodo);

        title = '';
    };
</script>

<style>
</style>

<form on:submit={onSubmit}>
    <div class="form-group">
        <input
            type="text"
            name="title"
            class="form-control"
            placeholder="Title"
            bind:value={title} />
        <button class="btn btn-primary mt-3">Add Todo</button>
    </div>
</form>
