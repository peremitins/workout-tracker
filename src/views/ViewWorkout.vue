<template>
	<div></div>
</template>

<script>
import { ref } from "vue";
import { useRoute } from "vue-router";
import { supabase } from "../supabase/init";

export default {
	name: "View-Workout",
	setup() {
		const route = useRoute();
		const data = ref(null);
		const dataLoaded = ref(null);
		const errorMsg = ref(null);
		const statusMsg = ref(null);

		const currentId = route.params.workoutId;

		const getData = async () => {
			try {
				const { data: workouts, error } = await supabase
					.from("workouts")
					.select("*")
					.eq("id", currentId);
				if (error) throw error;
				data.value = workouts;
				dataLoaded.value = true;
			} catch (error) {
				errorMsg.value = error.message;
				setTimeout(() => {
					errorMsg.value = false;
				}, 4000);
			}
		};

		getData();
		return {
			data,
			dataLoaded,
			errorMsg,
			statusMsg
		};
	}
};
</script>

<style>
</style>