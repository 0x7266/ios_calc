<script lang="ts">
	const buttons = [
		["C", "~", "%", "/"],
		[7, 8, 9, "x"],
		[4, 5, 6, "-"],
		[1, 2, 3, "+"],
		[0, ".", "="],
	];
</script>

<main>
	<div class="display" />
	<div class="buttons">
		{#each buttons as row, index (index)}
			{#each row as button (button)}
				<button>{button}</button>
			{/each}
		{/each}
	</div>
</main>

<style scoped>
	main {
		background-color: black;
		display: grid;
		min-height: 100vh;
		place-content: center;
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
