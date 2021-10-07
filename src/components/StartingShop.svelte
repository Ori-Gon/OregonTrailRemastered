<script>
    import { createEventDispatcher } from 'svelte';

    let selectedItem = "";

    let itemData = {
        oxen: {
            amount: 1,
            min: 1,
            max: 20
        },
        food: {
            amount: 15,
            min: 15,
            max: 2000
        },
        clothing: {
            amount: 0,
            min: 0,
            max: 20
        },
        ammo: {
            amount: 0,
            min: 0,
            max: 2000
        },
        spare_parts: {
            amount: 0,
            min: 0,
            max: 30
        }
    }

	const dispatch = createEventDispatcher();
    function dispatchBoughtItems() {
		dispatch('message', );
	}

    function fixAmount() {
        if (itemData[selectedItem].max < itemData[selectedItem].amount) {
            itemData[selectedItem].amount = itemData[selectedItem].max;
        }
        else if (itemData[selectedItem].min > itemData[selectedItem].amount) {
            itemData[selectedItem].amount = itemData[selectedItem].min;
        }
    }
</script>
<h2>
    Shop:
</h2>   
<button on:click={function() {selectedItem="oxen"}}>Oxen</button>
<button on:click={function() {selectedItem="food"}}>Food</button>
<button on:click={function() {selectedItem="clothing"}}>Clothing</button>
<button on:click={function() {selectedItem="ammo"}}>Ammo</button>
<button on:click={function() {selectedItem="spare_parts"}}>Spare Parts</button>

{#if selectedItem !== ""}
<h2>How much {selectedItem} do you want?</h2>
<input bind:value={itemData[selectedItem].amount} on:change={fixAmount}  type="number" max={itemData[selectedItem].max} min={itemData[selectedItem].min}>
{/if}
<button on:click={dispatchBoughtItems}>Exit shop</button>