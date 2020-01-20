<template>
	<div class="SpecialListPage">
		<div class="SpecialListPage-header">
			<div>
				<span class="SpecialListPage-title">全部专题</span>
			</div>
		</div>
		<div class="SpecialListPage-body">
			<div>
				<div class="SpecialListCard SpecialListPage-specialCard" v-for="(item, index) in specials" :key="index">
					<div class="SpecialListCard-banner"><img :src="item.banner" alt="" /></div>
					<div class="SpecialListCard-body">
						<div class="SpecialListCard-header">
							<div class="SpecialListCard-infos">
								<a href="" class="SpecialListCard-title">{{ item.title }}</a>
								<div class="SpecialListCard-relatedInfo">
									<span>{{ item.updated }}更新 · {{ item.viewCount }}次浏览</span>
								</div>
							</div>
						</div>
						<a href="" class="SpecialListCard-intro">{{ item.introduction }}</a>
						<div class="SpecialListCard-sections">
							<a href="" v-for="(section, index) in item.sections" :key="index">{{ section.sectionTitle }}</a>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>


<script>
	export default {
		name: 'special',
		data() {
			return {
				specials: []
			};
	},
	created() {
		this.axios.get('http://localhost:8080/api/special/all').then(res => {
			console.log(res);
			this.specials = res.data.data;
		});
	}
};
</script>

<style lang="scss" scoped>
	.SpecialListPage {
		display: block;
		.SpecialListPage-header {
			background: #fff;
			box-shadow: 0 1px 3px 0 rgba(26,26,26,.1);
			.SpecialListPage-title {
				margin-left: 12px;
				font-size: 25px;
				font-weight: 600;
			}
		}
		.SpecialListPage-header>div {
			display: flex;
			align-items: center;
			margin: 0 auto;
			width: 1000px;
			height: 100px;
		}
		.SpecialListPage-body {
			width: 1000px;
			margin: 10px auto 0;
			.SpecialListCard {
				display: flex;
				width: 1000px;
				height: 188px;
				border-radius: 3px;
				box-shadow: 0 1px 3px 0 rgba(26,26,26,.1);
				background-color: #fff;
				box-sizing: border-box;
				padding: 24px;
				.SpecialListCard-banner {
					flex-shrink: 0;
					width: 336px;
					height: 140px;
					border-radius: 4px;
					overflow: hidden;
					img {
						object-fit: cover;
						width: 100%;
						height: 100%;
					}
				}
				.SpecialListCard-body {
					flex: 1 1;
					margin-left: 20px;
					overflow: hidden;
					.SpecialListCard-header {
						display: flex;
						.SpecialListCard-infos {
							flex: 1 1;
							overflow: hidden;
							.SpecialListCard-title {
								display: block;
								height: 28px;
								line-height: 28px;
								font-size: 20px;
								white-space: nowrap;
								overflow: hidden;
								text-overflow: ellipsis;
								font-weight: 600;
							}
							.SpecialListCard-relatedInfo {
								display: flex;
								align-items: center;
								margin-top: 10px;
								font-size: 12px;
								height: 17px;
								color: #999;
							}
						}
					}
					.SpecialListCard-intro {
						margin-top: 8px;
						max-height: 42px;
						line-height: 21px;
						color: #444;
						display: -webkit-box;
						text-overflow: hidden;
						overflow: hidden;
						-webkit-line-clamp: 2;
						-webkit-box-orient: vertical;
					}
					.SpecialListCard-sections {
						display: flex;
						flex-wrap: wrap;
						margin-top: 12px;
						height: 24px;
						overflow: hidden;
						a {
						    -ms-flex-negative: 0;
						    flex-shrink: 0;
						    padding: 0 8px;
						    max-width: 580px;
						    height: 24px;
						    line-height: 24px;
						    border-radius: 5px;
						    background-color: #f6f6f6;
						    color: #8590a6;
						    font-size: 12px;
						    white-space: nowrap;
						    overflow: hidden;
						    text-overflow: ellipsis;
						}
						a+a {
							margin-left: 12px;
						}
					}
				}
			}
		}
	}
</style>
