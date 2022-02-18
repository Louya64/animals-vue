<template>
	<label class="formItemLabel" :for="label">{{ labelFr }}</label>
	<select
		:value="modelValue"
		@input="$emit('update:modelValue', $event.target.value)"
		class="formItemField select"
		:id="label"
	>
		<option disabled value="">{{ optionEmpty }}</option>
		<option v-for="option in options" :value="option">{{ option }}</option>
	</select>
</template>

<script>
export default {
	props: ["labelFr", "label", "modelValue", "optionEmpty", "options"],
	emits: ["update:modelValue"],
	mounted() {
		console.log(this.options);
	},
};
</script>
