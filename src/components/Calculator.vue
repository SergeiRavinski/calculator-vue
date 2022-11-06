<template>
	<section class="calculator">
		<div class="calculator__output">
			{{ showingResult ? currentResult : currentInput }} 
		</div>
		<button @click="clearResult" class="button__1">C</button>
		<button @click="handleOperatorInput('/')" class="button__2">/</button>
		<button @click="handleDigitInput(7)" class="button__3">7</button>
		<button @click="handleDigitInput(8)" class="button__4">8</button>
		<button @click="handleDigitInput(9)" class="button__5">9</button>
		<button @click="handleOperatorInput('*')" class="button__6">*</button>
		<button @click="handleDigitInput(4)" class="button__7">4</button>
		<button @click="handleDigitInput(5)" class="button__8">5</button>
		<button @click="handleDigitInput(6)" class="button__9">6</button>
		<button @click="handleOperatorInput('-')" class="button__10">-</button>
		<button @click="handleDigitInput(1)" class="button__11">1</button>
		<button @click="handleDigitInput(2)" class="button__12">2</button>
		<button @click="handleDigitInput(3)" class="button__13">3</button>
		<button @click="handleOperatorInput('+')" class="button__14">+</button>
		<button @click="handleDigitInput(0)" class="button__15">0</button>
		<button @click="handleDigitInput('.')" class="button__16">.</button>
		<button @click="handleEqualsInput" class="button__17">=</button>
	</section>	
</template>

<script>
export default {
		data() {
			return {
				currentResult: 0,
				currentInput: '',
				currentOperator: null,
				showingResult: true,
			}
		},

		//created() {
		//	window.addEventListener('keyup', this.handleKeyUp);
		//},
		
		computed: {
			currentInputAsNumber() {
				return Number(this.currentInput)
			}
		},

		methods: {
			calculateResult() {
				switch(this.currentOperator) {
					case '+':
						this.currentResult += this.currentInputAsNumber;
						break;
					case '-':
						this.currentResult -= this.currentInputAsNumber;
						break;
					case '/':
						this.currentResult /= this.currentInputAsNumber;
						break;
					case '*':
						this.currentResult *= this.currentInputAsNumber;
						break;
					default:
						this.currentResult = this.currentInputAsNumber;
						break;
				}
			},

			clearResult() {
				this.currentResult = 0;
				this.currentInput = '';
				this.currentOperator = null;
				this.showingResult = true;
			},
			
			handleOperatorInput(operator) {
				this.calculateResult();
				this.currentOperator = operator;
				this.currentInput = '';
				this.showingResult = true;
			},

			handleDigitInput(digit) {
				this.currentInput += digit;
				this.showingResult = false;
			},
			
			handleEqualsInput() {
				this.calculateResult();
				this.showingResult = true;
				this.currentInput = '';
			},

			handleKeyUp(event) {
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
						this.handleDigitInput(event.key);
						break;
					case '+':
					case '-':
					case '/':
					case '*':
						this.handleOperatorInput(event.key);
						break;
					case '.':
					case ',':
						this.handleDigitInput('.');
						break;
					case '=':
					case 'Enter':
						this.handleEqualsInput();
						break;
					case 'Escape':
					case 'Backspace':
						this.clearResult();
						break;
				}
			}	
		}
	}

</script>

<style>
	.calculator {
		margin: 2rem auto;
		width: 435px;
		height: 645px;
		background-color: #feffff;;
		box-shadow: 3px 3px 10px 2px rgba(166, 166, 170, 0.75);
		border-radius: 5px;
		display: grid;
		grid-template-columns: 10px 100px 5px 100px 5px 100px 5px 100px 10px;
		grid-template-rows: 10px 100px 5px 100px 5px 100px 5px 100px 5px 100px 5px 100px 10px;
	}

	button {
		border: 1px black;
		background-color: rgb(233, 232, 232);
		border-radius: 5px;
		color: #455A73B2;
		font-size: 2.5rem;
		cursor: pointer;
	}

	button:hover {
		background-color: rgb(206, 208, 221);
		opacity: 0.8;
	}

	button:active {
		color: black;
	}

	.calculator__output {
		grid-column: 2/9;
		grid-row: 2/3;
		background-color: black;
		color: white;
		padding: 1.5rem;
		font-size: 3rem;
		border-radius: 5px;
		overflow: hidden;
	}

	.button__1 {
		grid-column: 2/7;
		grid-row: 4/5;
		background: #bdbdbd;
	}

	.button__2 {
		grid-column: 8/9;
		grid-row: 4/5;
		background: #F7B432;
		color: white;
	}

	.button__3 {
		grid-column: 2/3;
		grid-row: 6/7;
	}

	.button__4 {
		grid-column: 4/5;
		grid-row: 6/7;
	}

	.button__5 {
		grid-column: 6/7;
		grid-row: 6/7;
	}

	.button__6 {
		grid-column: 8/9;
		grid-row: 6/7;
		background: #F7B432;
		color: white;
	}

	.button__7 {
		grid-column: 2/3;
		grid-row: 8/9;
	}

	.button__8 {
		grid-column: 4/5;
		grid-row: 8/9;
	}

	.button__9 {
		grid-column: 6/7;
		grid-row: 8/9;
	}

	.button__10 {
		grid-column: 8/9;
		grid-row: 8/9;
		background: #F7B432;
		color: white;
	}

	.button__11 {
		grid-column: 2/3;
		grid-row: 10/11;
	}

	.button__12 {
		grid-column: 4/5;
		grid-row: 10/11;
	}

	.button__13 {
		grid-column: 6/7;
		grid-row: 10/11;
	}

	.button__14 {
		grid-column: 8/9;
		grid-row: 10/11;
		background: #F7B432;
		color: white;
	}

	.button__15 {
		grid-column: 2/5;
		grid-row: 12/13;
	}

	.button__16 {
		grid-column: 6/7;
		grid-row: 12/13;
	}
	
	.button__17 {
		grid-column: 8/9;
		grid-row: 12/13;
		background: #F7B432;
		color: white;
	}
</style>