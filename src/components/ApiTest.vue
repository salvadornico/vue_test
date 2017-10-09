<template lang="pug">
#api-test
	h1 API test
	button(v-on:click="fetchData()") Get data
	.results
		span Results go here:
		br
		span {{ title }}
		br
		span {{ greeting }}
</template>

<script>
export default {
	name: "api-test",
	data() {
		return {
			title: "",
			greeting: ""
		}
	},
	methods: {
		fetchData: function() {
			this.title = "Fetching data.."
			fetch('http://127.0.0.1:5000/json')
				.then(response => response.json())
				.then(data => {
					this.title = data.title
					this.greeting = data.greeting
				})
		}
	}
}
</script>

