<template>
<div class="component">
	<h1> Simple AJAX </h1>
	<button v-on:click="sendRequest"> Send request </button>
	<p> {{message}} </p>
</div>
</template>

<script>
export default {
	data: () => ({
		message: 'No response yet'
	}),
	methods: {
		async sendRequest() {
			const url = 'https://forverkliga.se/JavaScript/api/simple.php?key=value'
			try {
				// Fetch skickar ett GET request till URL
				const response = await fetch(url)
				const data = await response.json()
				console.log('Data from API:', data);
				this.message = `Message: ${data.message}. Time: ${data.time}`
			}
			catch(error) {
				this.message = 'Something went wrong. Please try again later.'
			}
		}  // sendRequest
	}  // methods
}
</script>

<style scoped>
.component {
	border: 1px solid gray;
	padding: 1em;
	margin: 1em;
	background: #ACD7F9;
}
</style>
