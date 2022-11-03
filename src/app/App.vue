<template>
	<Calculator/>
	<Converter/>
	<!--<CalculatorSimple/>-->
	<!--<CalculatorAdvanced/>-->
</template>

<script>
	import Calculator from '../components/Calculator.vue';
	import Converter from '../components/Converter.vue';
	//import CalculatorSimple from '../components/CalculatorSimple.vue';
	//import CalculatorAdvanced from '../components/CalculatorAdvanced.vue';

	export default {
		components: {
    		Calculator,
			Converter,
			//CalculatorSimple,
			//CalculatorAdvanced,	
}
	}
</script>

<style>
	body {
		display: flex;
		justify-content: center;
	}
</style>