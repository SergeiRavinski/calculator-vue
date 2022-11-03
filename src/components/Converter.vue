<template>
	<section class="converter">
		<input class="converter__input" type="number" placeholder="mm" v-model="valueMM" />
		<div class="converter__output">{{ valueCM }} cm</div>
		<input class="converter__input" type="number" placeholder="cm" v-model="valueCM" />
		<div class="converter__output">{{ valueM }} m</div>
		<input class="converter__input" type="number" placeholder="m" v-model="valueM" />
		<div class="converter__output">{{ valueKM }} km</div>
	</section>
	
</template>

<script>
	export default {
		data() {
			return {
				valueMM: 0,
				valueCM: 0,
				valueM: 0,
			}
		},

		computed: {
			valueCM() {
				return (this.valueMM / 10);
			},
			valueM() {
				return (this.valueCM / 100);
			},
			valueKM() {
				return (this.valueM / 1000);
			}
		},	
	}



</script>

<style>
	.converter {
		position: absolute;
		background: #feffff;
		width: 20rem;
		height: 15rem;
		margin: 1rem auto 2rem auto;
		box-shadow: 3px 3px 10px 2px rgba(166, 166, 170, 0.75);
		border-radius: 5px;
		width: 435px;
	}

	.converter__output {
		display: inline;
		margin: 1rem 1rem 1rem 2rem;
		border: 1px solid gray;
		padding: 0.3rem;
		overflow: scroll;


	}

	.converter__input {
		height: 0.2rem;
		padding: 0.8rem;
		border-radius: 0.3rem;
		overflow: scroll;
		margin: 1.4rem;
		font-size: 1rem;
	}

</style>
