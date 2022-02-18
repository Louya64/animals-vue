<template>
	<label class="formItemLabel" :for="label">{{ labelFr }}</label>
	<input
		:value="modelValue"
		class="formItemField"
		type="number"
		:id="label"
		@input="$emit('update:modelValue', Number($event.target.value))"
	/>
</template>

<script>
export default {
	props: ["labelFr", "label", "modelValue"],
	emits: ["update:modelValue"],
};
</script>
