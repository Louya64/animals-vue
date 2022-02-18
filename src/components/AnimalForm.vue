<template>
	<h2>{{ animal.name === "" ? "Animal n°" + (index + 1) : animal.name }}</h2>
	<div class="formItem">
		<TextInput
			labelFr="Nom de l'animal"
			label="animalName"
			v-model="animal.name"
		/>
	</div>

	<div class="formItem">
		<NumberInput
			labelFr="Age de l'animal"
			label="animalAge"
			v-model="animal.age"
		/>
	</div>

	<div class="formItem">
		<SelectInput
			labelFr="Quel animal ?"
			label="animalType"
			v-model="animal.type"
			optionEmpty="Sélectionnez un animal"
			:options="animalsArray"
		/>
	</div>

	<p>==================</p>
</template>

<script>
import TextInput from "./TextInput.vue";
import NumberInput from "./NumberInput.vue";
import SelectInput from "./SelectInput.vue";
export default {
	props: ["index"],
	data() {
		return {
			animal: {
				name: "",
				age: null,
				type: "",
			},
			animalsArray: ["chat", "chien", "lapin"],
		};
	},
	updated() {
		this.$emit("animal-infos", { animal: this.animal, index: this.index });
	},
	components: { TextInput, NumberInput, SelectInput },
};
</script>

<style>
.select {
	background-color: lightblue !important;
}
</style>
