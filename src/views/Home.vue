<template>
  <div class="container">
	<ul class="tab-list">
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
	<!-- 二级路由入口 -->
	<router-view />
  </div>
</template>

<script>
export default {
	name: 'home',
	data() {
		return {};
	},
	created() {}
};
</script>
<style lang="scss" scoped>
	.container {
		padding-left: 10%;
		padding-right: 10%;
		width: 80%;
		box-sizing: border-box;
		.tab-list{
			width: 100%;
			height: 45px;
			line-height: 45px;
			background: #fff;
			float: left;
			margin-bottom: 5px;
			li {
				float: left;
				width: 54px;
			}
			li:nth-child(1){
				padding-left: 100px;
			}
		}
	}
</style>
