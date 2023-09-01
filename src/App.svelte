<script lang="ts">
	const buttons = [
		["C", "⁺∕₋", "%", "/"],
		["7", "8", "9", "x"],
		["4", "5", "6", "-"],
		["1", "2", "3", "+"],
		["0", ".", "="],
	];
	let display: string = "0";
	let currentValue = "";
	function handleCLick(button: string) {
		if (button === "=") {
			calculate(display);
			return;
		}
		if ((currentValue.includes(".") || currentValue === "") && button === ".") {
			return;
		}

		if (["C", "⁺∕₋", "%", "/", "x", "-", "+", "="].includes(button)) {
			currentValue = "";
			display = display === "0" ? button : `${display}${button}`;
			return;
		}

		display = display === "0" ? button : `${display}${button}`;
		currentValue += button;
	}

	function calculate(calculation: string) {
		console.log(calculation.split(/[\+\-\/x]/g));
	}
</script>

<main>
	<div class="calc">
		<div class="display">{display}</div>
		<div class="buttons">
			{#each buttons as row, i (i)}
				{#each row as button, j (button)}
					<button
						on:click={() => handleCLick(button)}
						class={i === 0 && j !== 3
							? "btn-3"
							: j === 3 || button === "="
							? "btn-2"
							: button === "0"
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
		gap: 6vh;
		padding: 3vh 2rem;
		overflow: hidden;
		width: 30vw;
	}

	.display {
		color: white;
		display: flex;
		flex-direction: row-reverse;
		font-size: 9rem;
		padding: 0 1.4rem;
		overflow: hidden;
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

	@media (width < 1800px) {
		main {
			max-height: 100dvh;
		}

		.calc {
			max-height: 90dvh;
			padding: 3vh 0.7rem;
			width: 90vw;
			max-width: 400px;
		}

		.display {
			font-size: 4rem;
		}

		.buttons {
			gap: 10px;
		}

		button {
			font-size: 1.4rem;
			padding: 1rem 1rem;
		}
	}
</style>
