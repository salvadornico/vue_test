<template lang="pug">

.users
	h1 Users
	table
		tr
			th Name
			th Email
			th Schwifty?
			th Delete
		tr(v-for="user in users")
			td
				span(:class="{schwifty: user.isSchwifty}") {{user.name}}
			td
				span(:class="{schwifty: user.isSchwifty}") {{user.email}}
			td
				input.toggle(type="checkbox" v-model="user.isSchwifty")
			td
				button(v-on:click="deleteUser(user)") X
	br
	br
	form(v-on:submit="addUser")
		input(type="text" v-model="newUser.name" placeholder="Enter name")
		br
		input(type="email" v-model="newUser.email" placeholder="Enter email")
		br
		input(type="submit" value="Submit")

</template>

<script>

export default {
	name: "users",
	data() {
		return {
			newUser: {},
			users: []
		}
	},
	methods: {
		addUser: function(e) {
			this.users.push({
				name: this.newUser.name,
				email: this.newUser.email,
				isSchwifty: false
			})
			e.preventDefault()
		},
		deleteUser: function(user) {
			this.users.splice(this.users.indexOf(user), 1)
		}
	},
	created: function() {
		this.$http.get("https://jsonplaceholder.typicode.com/users")
			.then(function(response) {
				this.users = response.data;
			})
	}
}

</script>

<style lang="stylus" scoped>
table {
	position: relative;
	left: 50%;
	transform: translateX(-50%);

	.schwifty {
		text-decoration: line-through;
	}
}
</style>

