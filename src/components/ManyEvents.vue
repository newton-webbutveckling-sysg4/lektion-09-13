<template>
<div>
	<h2> I have many events </h2>
	<button v-on:click="eventTrigger1"> Trigger event #1 </button>
	<button v-on:click="eventTrigger2"> Trigger event #2 </button>
	<button v-on:click="eventTrigger3"> Trigger event #3 </button>
</div>
</template>

<script>
export default {
	methods: {
		eventTrigger1() {
			this.$emit('event1', 'Event #1')
		},
		eventTrigger2() {
			this.$emit('event2', 'Event #2')
		},
		eventTrigger3() {
			this.$emit('event3', 'Event #3')
		}
	}
}
</script>

<style scoped>

</style>
