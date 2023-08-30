<script lang="ts">
	const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9];
	const operators = ["+", "-", "x", "/"];
	const otherButtons = ["C", "~", "%"];
	const buttons = [
		["C", "~", "%", "/"],
		[7, 8, 9, "x"],
		[4, 5, 6, "-"],
		[1, 2, 3, "+"],
		[0, ".", "="],
	];
</script>

<main>
	<div class="calc">
		<div class="display" />
		<div class="buttons">
			{#each buttons as row}
				{#each row as button}
					<button>{button}</button>
				{/each}
			{/each}
		</div>
	</div>
</main>

<style scoped>
	main {
		background-color: black;
		display: grid;
		min-height: 100vh;
		place-content: center;
	}

	.calc {
		/* border: solid white; */
	}

	.display {
		height: 10vh;
		border: solid white;
	}

	.buttons {
		display: grid;
		grid-template-columns: 1fr 1fr 1fr 1fr;
		gap: 1px;
	}

	button {
		background-color: #334141;
		border-radius: 10px;
		font-size: 3rem;
		padding: 1rem 2rem;
	}
</style>
