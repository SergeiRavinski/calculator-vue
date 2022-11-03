<template>
	<section class="calculator-simple">
		<div class="calculator-simple__output">
			{{ showingResult ? total : sequence }}
		</div>

		<div class="calculator-simple__input">
			<div class="calculator-simple__digits">
				<button @click="clearResult" class="calculator-simple__button calculator-simple__clear">C</button>
				<button @click="handleDigitInput(n)" class="calculator-simple__button calculator-simple__digit" v-for="n in 9">{{ n }}</button>
				<button @click="handleDigitInput(0)" class="calculator-simple__button calculator-simple__digit calculator-simple__zero">0</button>
				<button @click="handleDecimalInput('.')" class="calculator-simple__button">,</button>
			</div>
			
			<div class="calculator-simple__operators">
				<button @click="handleOperatorInput('/')" class="calculator-simple__button calculator-simple__operator">/</button>
				<button @click="handleOperatorInput('*')" class="calculator-simple__button calculator-simple__operator">*</button>
				<button @click="handleOperatorInput('-')" class="calculator-simple__button calculator-simple__operator">-</button>
				<button @click="handleOperatorInput('+')" class="calculator-simple__button calculator-simple__operator">+</button>
				<button @click="showResult" class="calculator-simple__button">=</button>
			</div>
		</div>

		<div class="calculator-simple__info">
			<div>sequence: {{ sequence }}</div>
			<div>total: {{ total }}</div>
		</div>
	</section>
</template>

<script>
	export default {
		data() {
			return {
				sequence: '',
				total: 0,
				showingResult: false
			}
		},

		created() {
			window.addEventListener('keyup', this.handleKeyup);
		},
		
		methods: {
			clearResult() {
				this.sequence = '';
				this.total = 0;
				this.showingResult = false;
			},

			calculateResult() {
				this.total = eval(this.sequence)
			},
			
			handleInput(input) {
				this.sequence += input;
			},
			
			showResult() {
				this.calculateResult();
				this.showingResult = true;
			},

			handleKeyup(event) {
				switch(event.key) {
					case '0':
					case '1':
					case '2':
					case '3':
					case '4':
					case '5':
					case '6':
					case '7':
					case '8':
					case '9':
					case '+':
					case '-':
					case '/':
					case '*':
					case '.':
					case ',':
						this.handleInput(event.key)
						break;
					case '=':
					case 'Enter':
						this.showResult()
						break;
					case 'Escape':
					case 'Backspace':
						this.clearResult()
						break;
				}
			}
		}
	}
</script>

<style>
	.calculator-simple {
		--background: blue;
		--foreground: white;
		--secondary: lightgray;
		--gap: 0.5em;
		--font-size-large: 3em;
		--font-size-medium: 1.5em;
	}

	body {
		background: var(--background);
		color: var(--foreground)
	}

	.calculator-simple {
		position: relative;
		margin: 10px;
		display: flex;
		flex-flow: column nowrap;
		width: 20em;
		height: 35em;
		border: 2px solid var(--secondary);
		border-radius: 5px;
		padding: 1em;
		background: var(--background);
		color: var(--foreground);
		font-family: "Courier New";
	}

	.calculator-simple__info {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		transform: translateX(calc(100% + 1em));
		background: var(--foreground);
		color: var(--background);
		border: 2px solid var(--secondary);
		font-family: monospace;
		padding: 0.5em;
		border-radius: 5px;
	}

	.calculator-simple__output {
		font-size: 3em;
		width: 100%;
		min-height: 3em;
		border: 2px solid var(--secondary);
		border-radius: 5px;
		padding: 0.5em;
		margin-bottom: 0.5em;
		overflow: scroll;
		text-align: right;
		/* text-overflow: ellipsis; */
		white-space: nowrap;
	}

	.calculator-simple__input {
		display: flex;
		gap: var(--gap);
		height: 100%;
	}

	.calculator-simple__digits {
		display: grid;
		width: 80%;
		grid-template-columns: repeat(3, 1fr);
		gap: var(--gap);
	}

	.calculator-simple__operators {
		display: flex;
		height: 100%;
		width: 20%;
		flex-flow: column nowrap;
		column-gap: 0.5em;
		row-gap: 0.5em;
	}
	
	.calculator-simple__button {
		font-size: 1.5em;
		width: 100%;
		height: 100%;
		border: 2px solid lightgray;
		border-radius: 5px;
		padding: 0.5em;
	}

	.calculator-simple__button:hover {
		background: var(--foreground);
		color: var(--background);
		border-color: var(--background)
	}

	.calculator-simple__button:active {
		background: var(--secondary);
		color: var(--foreground);
	}

	.calculator-simple__zero {
		grid-column: span 2;
	}

	.calculator-simple__clear {
		grid-column: span 3;
	}
</style>