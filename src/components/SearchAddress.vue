<template>
  <div class="hello">
		<input
			class="main-input"
			v-model="cep"
			type="number"
			name="cep"
			placeholder="Digite um cep para buscar..."
		>
		<h1>{{ cep }}</h1>
  </div>
</template>

<script>
/*eslint no-unused-vars: "warn"*/
import axios from 'axios'

export default {
  name: 'SearchAddress',
	data() {
		return {
			cep: null,
			addresses: null
		}
	},
	methods: {  },
	async created() {
		this.addresses = await axios
				.get('http://localhost:8000/api/v1/address/')
				.then(res => res.data)
				.catch(err => console.log(err.message))

		console.log(this.addresses)
	}
}
</script>

<style scoped>
  .main-input {
		width: 200px;
		height: 10px;
		border-radius: 12px;
		padding: 10px;
	}
	h3 {
		margin: 40px 0 0;
	}
	ul {
		list-style-type: none;
		padding: 0;
	}
	li {
		display: inline-block;
		margin: 0 10px;
	}
	a {
		color: #42b983;
	}
</style>
