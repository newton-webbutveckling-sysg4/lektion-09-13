<template>
	<div class="hello">
		<h1> Hello! </h1>
		<p> {{message}} </p>
		<ManyEvents
			v-on:event1="handleEvent"
			v-on:event2="handleEvent"
			v-on:event3="handleEvent"
			></ManyEvents>
	</div>
</template>

<script>
import ManyEvents from './ManyEvents.vue'

export default {
	name: 'HelloWorld',
	components: {
		ManyEvents
	},
	data: () => ({
		message: 'No message'
	}),
	methods: {
		handleEvent(data) {
			this.message = data
		}
	},
	props: {
		msg: String
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
