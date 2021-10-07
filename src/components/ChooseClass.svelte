<script>
    import { createEventDispatcher } from 'svelte';

    let selectedClass = "";

	const dispatch = createEventDispatcher();
    function dispatchClass() {
		dispatch('message', selectedClass);
	}

</script>
<h2>
    You may be: 
    <button on:click={function() {selectedClass="banker"}}>1. Be a banker</button>
    <button on:click={function() {selectedClass="carpenter"}}>2. Be a carpenter</button>
    <button on:click={function() {selectedClass="farmer"}}>3. Be a farmer</button>
    <button on:click={dispatchClass}>Confirm that you want to {selectedClass}</button>
</h2>   