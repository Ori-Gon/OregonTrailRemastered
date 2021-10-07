<script>
    import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();
    function dispatchStart() {
		dispatch('message');
	}
</script>
<h2>
    <button on:click={dispatchStart}>Start</button>
</h2>   