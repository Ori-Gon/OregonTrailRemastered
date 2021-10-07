<script >
	import StartScreen from "./components/StartScreen.svelte";
	import ChooseClass from "./components/ChooseClass.svelte";
	import ChooseNames from "./components/ChooseNames.svelte";
	import StartingShop from "./components/StartingShop.svelte";

	let currentScreen = "start";
	let playerClass = "";
	let playerNames = [];

	function action() {
		if (currentScreen === "start") {
			currentScreen = "chooseClass";
			inputType = inputTypes.numbers;
		}
		else if (currentScreen === "chooseClass") {
			currentScreen = "chooseNames";
			inputType = inputTypes;
			inputEnabled = false;

			if (input === "1") {
				playerClass = "banker";
			}
			else if (input == "2") {
				playerClass = "carpenter";
			}
			else if (input == "3") {
				playerClass = "farmer";
			}
			else {
				alert("Not a choice");
				currentScreen = "ChooseClass"
				inputEnabled = true;
			}
		}
		resetInput();
	}

	function start(event) {
		currentScreen = "chooseClass";
	}
	function setClass(event) {
		playerClass = event.detail;
		currentScreen = "chooseNames";
	}
	function setNames(event) {
		playerNames = event.detail;
		currentScreen = "startingShop";
	}
	function setBoughtItems(event) {
		currentScreen = ""
	}
</script>

<h1>The Oregon Trail</h1>
{#if currentScreen === "start"}
	<StartScreen on:message={start}/>
{:else if currentScreen === "chooseClass"}
	<ChooseClass on:message={setClass}/>
{:else if currentScreen === "chooseNames"}
	<ChooseNames on:message={setNames}/>
{:else if currentScreen === "startingShop"}
	<StartingShop on:message={setBoughtItems}/>
{/if}