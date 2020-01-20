<template>
	<div class="roundTablePage">
		<div class="banner">
			<div class="banner-txt">圆桌</div>
		</div>
		<div class="container">
			<a href="" target="_blank" class="roundtableItem" v-for="(item, index) in roundtables" :key="index">
				<div class="roundtableItem-image">
					<img :src="item.banner" alt="" loading="lazy" />
				</div>
				<div class="roundtableItem-shadow"></div>
				<div class="roundtableItem-title">{{ item.name }}</div>
				<div class="roundtableItem-visitsCount">
						该圆桌被浏览 {{ item.visitsCount }} 次
				</div>
			</a>
		</div>
	</div>
</template>

<script>
	export default {
		name: 'roundtable',
		data() {
			return {
				roundtables: []
			};
	},
	created() {
		this.axios.get('http://localhost:8080/api/roundtable').then(res => {
			console.log(res);
			this.roundtables = res.data.data;
		});
	}
};
</script>

<style lang="scss" scoped>
	.main {
	    height: 29000px;
	}
	.roundTablePage {
		box-sizing: border-box;
		background-color: #fff;
		width: 1000px;
		margin: 10px auto;
		padding-bottom: 20px;
		border-radius: 2px;
		.banner {
			box-sizing: border-box;
			display: flex;
			padding: 20px;
			border-radius: 2px;
			box-shadow: 0 1px 3px 0 rgba(0,34,77,0.05);
			width: 1000px;
			height: 60px;
			margin-bottom: 10px;
			.banner-txt {
				box-sizing: border-box;
				margin: 0;
				font-weight: 600;
				color: #1a1a1a;
				font-size: 15px;
				line-height: 20px;
			}
		}
		.container {
			margin-bottom: 10px;
			padding: 0 20px;
			.roundtableItem {
				box-sizing: border-box;
				margin: 0;
				min-width: 0;
				width: 200px;
				height: 224px;
				position: relative;
				display: inline-block;
				margin-top: 20px;
				margin-right: 54px;
				.roundtableItem-image {
					box-sizing: border-box;
					margin: 0;
					max-width: 100%;
					height: 200px;
					width: 200px;
					position: relative;
					// border-radius: 6px;
					img {
						box-sizing: border-box;
						margin: 0;
						max-width: 100%;
						height: 200px;
						width: 200px;
						position: relative;
						border-radius: 6px;
					}
				}
				.roundtableItem-shadow {;
					box-sizing: border-box;
					margin: 0;
					border-radius: 6px;
					position: absolute;
					top: 0;
					width: 200px;
					height: 200px;
					left: 0;
					box-shadow: 0 2px 10px 0 rgba(0,0,0,0.1);
					background-image: linear-gradient(to bottom,rgba(0,0,0,0),rgba(0,0,0,0.5));
				}
				.roundtableItem-title {
					box-sizing: border-box;
					margin: 0;
					color: #fff;
					position: absolute;
					bottom: 34px;
					left: 10px;
				}
				.roundtableItem-visitsCount {
					box-sizing: border-box;
					margin: 0;
					color: #8590a6;
					margin-top: 10px;
					font-size: 14px;
					line-height: 1;
				}
			}
			.roundtableItem:nth-of-type(4n+2) {
			    margin-right: 52px;
			}
			.roundtableItem:nth-of-type(4n) {
			    margin-right: 0;
			}
			.roundtableItem:nth-of-type(n+5) {
			    margin-top: 40px;
			}
		}
	}
</style>
