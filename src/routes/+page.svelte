<script lang="ts">
	// import Counter from "./Counter.svelte";
	import TasksForm from "./TasksForm.svelte";

    //define a type
    type Task = {
        id: string;
        title: string;
        done: boolean;
    };

    let tasks = $state<Task[]>([]);

    function addTask(newTask: string) {
        tasks.push({
            id: crypto.randomUUID(),
            title: newTask,
            done: false
        });
    }

    function toggleDone(task: Task) {
        task.done = !task.done;
    }

</script>
<main>
    <h1>Welcome to Playground</h1>
    <TasksForm {addTask}/>
    <section>
        {#each tasks as task (task.id)}
            <article>
                <label>
                    <input checked={task.done} onchange={() => toggleDone(task)} type="checkbox" />
                </label>
                <span class:done={task.done}>{task.title}</span>
            </article>
        {/each}
    </section>
</main>

<style>
    main {
        margin: 1rem auto;
    }
    .done {
        text-decoration: line-through;
    }
</style>

<!-- <h1>Welcome to SvelteKit</h1> -->
<!-- <p>Visit <a href="https://svelte.dev/docs/kit">svelte.dev/docs/kit</a> to read the documentation</p> -->

<!-- <TasksForm></TasksForm> -->

<!-- <Counter max="4" onPop={ ()=>{alert("pop me")}}></Counter> -->