<template lang="pug">

.test
	h1 {{ title }}
	input(type="text" v-model="title")
	p(v-if="showName") This is {{ fullName }}
	p(v-else) Nobody
	ul
		li(v-for="item in items") {{ item.title }}

	input(type="text" v-model="greeting" v-on:keyup="pressKey" v-on:keyup.enter="enterHit")
	br
	button(v-on:click="greet(greeting)") Say Greeting
	br
	hr
	h3 {{ fullName }}
	label First Name:
	input(type="text" v-model="user.firstName")
	br
	label Last Name:
	input(type="text" v-model="user.lastName")
	hr
	h2 {{ msg }}

</template>

<script>

export default {
	name: "Test",
	props: {
		msg: {
			type: String,
			default: "Bloop"
		}
	},
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
	},
	computed: {
		fullName: function() {
			return `${this.user.firstName} ${this.user.lastName}`
		}
	}
}

</script>

<style lang="stylus" scoped>

.test
	position relative
	ul
		position relative
		left 50%
		transform translateX(-50%)
		width 200px

</style>
