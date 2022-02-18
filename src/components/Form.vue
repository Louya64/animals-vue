<template>
	<h1>form</h1>
	<form action="" @submit.prevent="submit">
		<p>Infos propriétaire</p>
		<p>===============================</p>
		<div class="formItem">
			<TextInput label-fr="Nom" label="firstname" v-model="person.firstname" />
		</div>

		<div class="formItem">
			<TextInput label-fr="Prénom" label="lastname" v-model="person.lastname" />
		</div>

		<div class="formItem">
			<NumberInput
				labelFr="Nombre d'animaux"
				label="nbAnimals"
				v-model="person.nbAnimals"
			/>
		</div>

		<p>===============================</p>
		<p>Infos {{ person.nbAnimals > 1 ? "animaux" : "animal" }}</p>
		<p>===============================</p>
		<AnimalForm
			:index="animal - 1"
			@animal-infos="updateAnimal"
			v-for="animal in person.nbAnimals"
		/>

		<button class="btn" type="submit">ajouter</button>
	</form>
</template>

<script>
import AnimalForm from "./AnimalForm.vue";
import TextInput from "./TextInput.vue";
import NumberInput from "./NumberInput.vue";
export default {
	data() {
		return {
			person: {
				firstname: "",
				lastname: "",
				nbAnimals: null,
			},
			animals: [],
		};
	},
	methods: {
		updtaNbAnimals() {
			for (let i = 0; i < this.person.nbAnimals; i++) {
				this.animals.push({
					name: "",
					age: null,
					type: "",
				});
			}
		},
		updateAnimal(animalToUpdate) {
			this.animals[animalToUpdate.index] = animalToUpdate.animal;
		},
		submit() {
			this.animals.map(
				(animal) => (animal.personFirstname = this.person.firstname)
			);
			this.$emit("add-animals", this.animals);
			this.$emit("add-people", { person: this.person });
			this.$emit("display-home");
			this.person = {
				firstname: "",
				lastname: "",
				nbAnimals: null,
			};
			this.animals = [];
		},
	},
	components: { AnimalForm, TextInput, NumberInput },
};
</script>

<style>
form {
	width: 20vw;
	margin: auto;
}
.formItem {
	background-color: rgba(173, 216, 230, 0.315);
	padding: 15px;
	border-radius: 5px;
	width: 100%;
	display: flex;
	justify-content: space-between;
	margin: 1.5vw auto;
}
.formItemField {
	background-color: transparent;
	width: 50%;
	border: none;
	border-bottom: 2px solid white;
}
</style>
