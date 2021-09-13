<template>
<div class="component">
	<h1> Sunrise and sunset times </h1>
	Where are you?
	(fylla i latitud och longitud)
	<button> Let's see </button>
	<p> {{ message }} </p>
	<p> {{ sunrise }} </p>
</div>
</template>

<script>
export default {
	data: () => ({
		// message: 'No results yet',
		errorMessage: '',
		dataFromApi: null
	}),
	computed: {
		sunrise() {
			if( !this.dataFromApi ) {
				return ''
			} else {
				return this.dataFromApi.results.sunrise
			}
		},
		sunset() {
			return this.dataFromApi ? this.dataFromApi.results.sunset : ''
		},
		message() {
			if( this.errorMessage ) {
				return this.errorMessage
			}
			else if( this.sunset && this.sunrise ) {
				return `The sun rose at ${this.sunrise} and sets at ${this.sunset} today. (+2h in Sweden)`
			} else {
				return 'No results yet.'
			}
		}
	},
	async mounted() {
		console.log('mounted');
		const lat = 57.701, lng = 11.912
		// @ 57.701511,11.9115471
		const url = `https://api.sunrise-sunset.org/json?lat=${lat}&lng=${lng}`
		let response
		this.errorMessage = ''
		try {
			response = await fetch(url)
			const data = await response.json()
			// console.log('Data from API', data);
			this.dataFromApi = data
		} catch(error) {
			if( response ) {
				this.errorMessage = 'Data is in the wrong format. Try again later.'
			} else {
				this.errorMessage = 'Could not send request. Check your internet connection?'
			}
		}
	}
}
</script>

<style scoped>
.component {
	border: 1px solid gray;
	padding: 1em;
	margin: 1em;
	background: #F9E5B6;
}
</style>
