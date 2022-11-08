<template>
	<Calculator/>
	<Converter/>
</template>

<script>
	import Calculator from '../components/Calculator.vue';
	import Converter from '../components/Converter.vue';

	export default {
		components: {
    		Calculator,
			Converter,
}
	}
</script>

<style>
	body {
		display: flex;
		justify-content: center;
	}
</style>