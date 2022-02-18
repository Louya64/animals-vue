<template>
	<h1>home</h1>
	<button class="btn" @click="displayForm">Ajouter un animal</button>
	<div
		class="personContainer"
		v-if="people.length > 0"
		v-for="person in people"
	>
		<h2 class="personName">{{ person.firstname }} {{ person.lastname }}</h2>
		<button class="btn" @click="displayDetails(person.firstname)">
			Voir les animaux
		</button>
	</div>
</template>

<script>
export default {
	props: {
		people: Array,
	},
	methods: {
		displayForm() {
			this.$emit("display-form");
		},
		displayDetails(name) {
			this.$emit("display-details", name);
		},
	},
};
</script>

<style>
.personContainer {
	width: 30%;
	margin: auto;
	display: flex;
	justify-content: space-between;
	align-items: center;
}
.personContainer .btn {
	margin: 0;
}
.personName {
	text-transform: capitalize;
	text-decoration: underline;
	font-size: 30px;
}
</style>
