<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
	<ul>
		<li>
			<router-link to="/home/recommoned">推荐</router-link>
		</li>
		<li>
			<router-link to="/home/follow">关注</router-link>
		</li>
		<li>
			<router-link to="/home/hot">热榜</router-link>
		</li>
	</ul>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
	name: 'home',
	data() {
		return {};
	},
	created() {}
};
</script>
<style lang="scss" scoped>
</style>
