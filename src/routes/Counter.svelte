<script lang="ts">
    let {max, onPop = ()=>{}} = $props()
    let count = $state(0);

    function increment() {
        count++;
        if(count > max) {
            count = max;
            onPop();
        }
    }

    function decrement() {
        count--;
        if(count < 0) {
            count = 0;
            onPop();
        }
    }

</script>

<button onclick={increment}> {count} </button>
<button onclick={decrement}> {count} </button>
