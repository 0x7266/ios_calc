<script lang="ts">
	const buttons = [
		["C", "⁺∕₋", "%", "/"],
		[7, 8, 9, "x"],
		[4, 5, 6, "-"],
		[1, 2, 3, "+"],
		[0, ".", "="],
	];
	let total: string = "0";
	function handleCLick(button: number | string) {
		total = `${total}${button}`;
	}
</script>

<main>
	<div class="calc">
		<div class="display">{total}</div>
		<div class="buttons">
			{#each buttons as row, i (i)}
				{#each row as button, j (button)}
					<button
						on:click={() => handleCLick(button)}
						class={i === 0 && j !== 3
							? "btn-3"
							: j === 3 || button === "="
							? "btn-2"
							: button === 0
							? "btn-lg btn-1"
							: "btn-1"}>{button}</button
					>
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
		font-family: Verdana, Geneva, Tahoma, sans-serif;
	}

	.calc {
		background-color: #1c1c1c;
		border-radius: 20px;
		display: flex;
		flex-direction: column;
		gap: 2vh;
		padding: 3vh 2vw;
	}

	.display {
		color: white;
		font-size: 9rem;
		padding: 0 2rem;
		text-align: end;
	}

	.buttons {
		display: grid;
		grid-template-columns: 1fr 1fr 1fr 1fr;
		gap: 1rem;
	}

	button {
		border: none;
		border-radius: 100%;
		font-size: 3rem;
		font-weight: bolder;
		padding: 2rem;
	}

	.btn-1 {
		background-color: #333333;
		color: white;
	}

	.btn-lg {
		grid-column: span 2;
		border-radius: calc(infinity * 1px);
		text-align: start;
		padding-left: 40px;
	}

	.btn-2 {
		background-color: #ff9500;
		color: white;
	}

	.btn-3 {
		background-color: #a5a5a5;
	}
</style>
