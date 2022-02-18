<template>
	<label class="formItemLabel" :for="label">{{ labelFr }}</label>
	<input
		:value="modelValue"
		class="formItemField"
		type="text"
		:id="label"
		@input="$emit('update:modelValue', $event.target.value)"
	/>
</template>

<script>
export default {
	props: {
		label: String,
		labelFr: String,
		modelValue: String,
	},
	emits: ["update:modelValue"],
};
</script>
