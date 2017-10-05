<template lang="pug">
.test
	input(type="text" v-model="title")
	h1 {{ title }}
	p(v-if="showName") {{ user.firstName }} {{ user.lastName }}
	p(v-else) Nobody
	ul
		li(v-for="item in items") {{ item.title }}

	input(type="text" v-model="greeting")
	br
	button(v-on:click="greet(greeting)") Say Greeting
	br
	br
	input(type="text" v-on:keyup="pressKey" v-on:keyup.enter="enterHit")
</template>

<script>
export default {
	name: "Test",
	data() {
		return {
			title: "Hello World",
			user: {
				firstName: "John",
				lastName: "Doe"
			},
			showName: true,
			items: [
				{ title: "Item One" },
				{ title: "Item Two" },
				{ title: "Item Three" },
			],
			greeting: ""
		}
	},
	methods: {
		greet: (greeting) => {
			alert(`Hello ${greeting}`)
		},
		pressKey: (e) => {
			console.log(e.target.value)
		},
		enterHit: () => {
			console.log("Ouch")
		}
	}
}
</script>

<style lang="stylus" scoped>

</style>
