<template>
	<div class="container">
		<h3>推荐</h3>
		<div class="list-right">
			<div class="right-top"></div>
			<div class="right-bottom"></div>
		</div>
	</div>
</template>

<script>
export default {
	name: 'recommoned',
	data() {
		return {};
	},
	created() {}	
};
</script>

<style lang="scss" scoped>
	.container {
		width: 100%;
		height: 500px;
		float: left;
		box-sizing: border-box;
		.list-right {
			width: 20%;
			float: right;
			.right-top {
				width: 100%;
				height: 30%;
				background: pink;
			}
			.right-bottom {
				width: 100%;
				height: 30%;
				background: green;
			}
		}
	}
</style>
