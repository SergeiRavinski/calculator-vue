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
			<input @input="handleInputKM" class="converter__input" type="number" placeholder="km" v-model="valueKM"/>
			<span>km</span>
		</div>
		<!--<div class="converter__output">{{ valueCM }} cm</div>
		<div class="converter__output">{{ valueM }} m</div>
		<div class="converter__output">{{ valueKM }} km</div>-->
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

		computed: {
			valueCM() {
				return (this.valueMM / 10);
			},
			valueM() {
				return ((this.valueMM / 10) / 100);
			},
			valueKM() {
				return (((this.valueMM / 10) / 100) / 1000);
			},

		methods: {
			handleInputMM() {

			},

			handleInputCM() {
					
			},

			handleInputM() {
					
			},
			
			handleInputKM() {
					
			},
				
			},
		}	
	}
</script>

<style>
	.converter {
		background: #F7B432;
		display: flex;
		flex-direction: column;
		color: black;
		width: 20rem;
		height: 15rem;
		margin: 1rem auto 2rem auto;
		box-shadow: 3px 3px 10px 2px rgba(166, 166, 170, 0.75);
		border-radius: 5px;
		width: 435px;
	}

	.converter__input {
		height: 0.5rem;
		width: 40%;
		padding: 0.8rem;
		border-radius: 0.3rem;
		overflow: scroll;
		margin: 0.7rem;
		font-size: 1rem;
	}
</style>
