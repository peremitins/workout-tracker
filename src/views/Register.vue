<template>
	<div>Reg</div>
</template>

<script>
import { ref } from "vue";

export default {
	setup() {
		const email = ref(null);
		const password = ref(null);
		const confirmPassword = ref(null);
		const errorMessage = ref(null);

		return {
			email,
			password,
			confirmPassword,
			errorMessage
		};
	}
};
</script>

<style>
</style>