<template lang="pug">
	#app
		test
</template>

<script>
import Test from "./components/Test"

export default {
	name: 'app',
	components: {
		Test
	}
}
</script>

<style lang="stylus">
#app
	font-family 'Avenir', Helvetica, Arial, sans-serif
	-webkit-font-smoothing antialiased
	-moz-osx-font-smoothing grayscale
	text-align center
	color #2c3e50
	margin-top 60px
</style>
