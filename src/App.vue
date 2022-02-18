<template>
	<div class="home" v-show="home">
		<Home
			@display-details="displayDetails"
			@display-form="displayForm"
			:people="people"
		/>
	</div>
	<div class="form" v-show="form">
		<Form
			@add-animals="pushAnimals"
			@add-people="pushPeople"
			@display-home="displayHome"
		/>
	</div>
	<div class="details" v-show="details">
		<Details
			@display-home="displayHome"
			:animals="animals"
			:personDetailsRequested="personDetailsRequested"
		/>
	</div>
</template>

<script>
import Home from "./components/Home.vue";
import Form from "./components/Form.vue";
import Details from "./components/Details.vue";
export default {
	data() {
		return {
			home: true,
			form: false,
			details: false,
			people: [],
			animals: [],
			personDetailsRequested: "",
		};
	},
	methods: {
		displayHome() {
			this.form = this.details = false;
			this.home = true;
		},
		displayForm() {
			this.home = this.details = false;
			this.form = true;
		},
		displayDetails(data) {
			this.personDetailsRequested = data;
			this.home = this.form = false;
			this.details = true;
		},
		pushPeople(data) {
			this.people.push(data.person);
		},
		pushAnimals(data) {
			data.map((animal) => this.animals.push(animal));
		},
	},
	components: { Home, Form, Details },
};
</script>

<style>
#app {
	text-align: center;
}
h1 {
	text-transform: capitalize;
	font-size: 30px;
}
.btn {
	padding: 10px 15px;
	margin: 5vh auto;
	background-color: lightblue;
	color: rgb(19, 19, 155);
	font-size: 20px;
	border: none;
	border-radius: 5px;
}
</style>
