<template>
	<section class="converter">
		<div class="converter__mm">
			<input @input="handleInputMM" class="converter__input" type="number" placeholder="mm" v-model="valueMM">
			<span>mm</span>
		</div>
		<div class="converter__cm">
			<input @input="handleInputCM" class="converter__input" type="number" placeholder="cm" v-model="valueCM"/>
			<span>cm</span>
		</div>
		<div class="converter__m">
			<input @input="handleInputM" class="converter__input" type="number" placeholder="m" v-model="valueM"/>
			<span>m</span>
		</div>
		<div class="converter__km">
			<input  @input="handleInputKM" class="converter__input" type="number" placeholder="km" v-model="valueKM"/>
			<span>km</span>
		</div>
	</section>
	
</template>

<script>
	export default {
		data() {
			return {
				valueMM: '',
				valueCM: '',
				valueM: '',
				valueKM: '',
			}
		},

		methods: {
			handleInputMM() {
				this.valueCM = this.valueMM / 10;  
				this.valueM = this.valueMM / 1000; 
				this.valueKM = this.valueMM / 1000000;
			},

			handleInputCM() {
				this.valueMM = this.valueCM * 10;
				this.valueM = this.valueCM / 100;
				this.valueKM = this.valueCM / 100000;
			},

			handleInputM() {
				this.valueMM = this.valueM * 1000;
				this.valueCM = this.valueM * 100;
				this.valueKM = this.valueM / 1000;	
			},
			
			handleInputKM() {
				this.valueMM = this.valueKM * 1000000;
				this.valueCM = this.valueKM * 100000;
				this.valueM = this.valueKM * 1000;
			},			
		},
	}	
	
</script>

<style>
	.converter {
		background: #F7B432;
		display: flex;
		flex-direction: column;
		color: #3b526f;
		width: 20rem;
		height: 15rem;
		margin: 1rem auto 2rem auto;
		box-shadow: 3px 3px 10px 2px rgba(166, 166, 170, 0.75);
		border-radius: 5px;
		width: 435px;
	}

	input:focus {
		text-shadow: 0.125rem 0.125rem 0.25rem rgb(175, 175, 175);
		transform: scale(1.015);
		transition-duration: 200ms;
		transition-timing-function: ease-in-out;
	}

	.converter__input {
		height: 0.5rem;
		width: 50%;
		padding: 0.8rem;
		border-radius: 0.3rem;
		overflow: scroll;
		margin: 0.7rem;
		font-size: 1rem;
	}
</style>
