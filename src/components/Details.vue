<template>
	<h1>
		Anima{{ animalsToDisplay.length > 1 ? "ux" : "l" }} de
		{{ personDetailsRequested }}
	</h1>
	<div v-for="animal in animalsToDisplay">
		<p>
			<span class="animalName">{{ animal.name }}</span> est un
			<span class="animalType">{{ animal.type }}</span> de
			<span class="animalAge">{{ animal.age }}</span> an{{
				animal.age > 1 ? "s" : ""
			}}
		</p>
	</div>
	<button @click="displayHome" class="btn">Retour à la liste complète</button>
</template>

<script>
export default {
	props: ["personDetailsRequested", "animals"],
	computed: {
		animalsToDisplay() {
			return this.animals.filter(
				(animal) => animal.personFirstname === this.personDetailsRequested
			);
		},
	},
	methods: {
		displayHome() {
			this.$emit("display-home");
		},
	},
};
</script>

<style>
.animalName {
	text-transform: capitalize;
	font-size: 25px;
	color: lightblue;
	font-weight: bold;
}
</style>
