<script>
    import Header from './components/Header.svelte';
    import Form from './components/Form.svelte';
    import Todolist from './components/Todolist.svelte';
    let todos = [];

    const addTodo = (e) => {
        todos = [...todos, e.detail];
    };

    const deleteTodo = (e) => {
        todos = todos.filter((todo) => todo.id !== e.detail);
    };

    const toggleTodo = (e) => {
        todos = todos.map((todo) => {
            if (todo.id === e.detail) {
                return {
                    ...todo,
                    completed: !todo.completed,
                };
            }
            return todo;
        });
    };
</script>

<style>
</style>

<main class="container">
    <Header />
    <Form on:addtodo={addTodo} />
    <Todolist {todos} on:deletetodo={deleteTodo} on:toggletodo={toggleTodo} />
</main>
