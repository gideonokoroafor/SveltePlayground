<script lang="ts">
    let newTask = $state("");
    let { addTask } : {
        addTask: (newTask: string) => void;
    } = $props();

    function formSubmitted(e: SubmitEvent) {
        e.preventDefault();
        addTask(newTask);
        newTask = "";
    }
</script>

<form onsubmit={formSubmitted}>
    <label for="">
        Task
        <input name="newTask" bind:value={newTask}/>
    </label>
    <button>Add</button>
</form>