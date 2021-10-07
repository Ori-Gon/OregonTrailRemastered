<script>
    import { createEventDispatcher } from 'svelte';

    let names = ["", "", "", "", ""];

	const dispatch = createEventDispatcher();
    function dispatchNames() {
		dispatch('message', names);
	}
</script>
<h2>
    What is your wagon mates going to be called be?
    <h4>1st person: <input type="text" bind:value={names[0]}/></h4>
    <h4>2nd person: <input type="text" bind:value={names[1]}/></h4>
    <h4>3rd person: <input type="text" bind:value={names[2]}/></h4>
    <h4>4th person: <input type="text" bind:value={names[3]}/></h4>
    <h4>5th person: <input type="text" bind:value={names[4]}/></h4>
    <button on:click={dispatchNames}>Confirm</button>
</h2>

<style>
    h4 {
        margin-left: 3rem;
    }
</style>