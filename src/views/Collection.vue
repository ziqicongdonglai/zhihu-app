<template>
	<div class="CollectionHotListPage">
		<div class="CollectionHotListPage-header">
			<div>
				<span class="CollectionHotListPage-title">热门收藏夹</span>
			</div>
		</div>
		<div class="CollectionHotListPage-body">
			<div>
				<div class="CollectionListCard CollectionHotListPage-CollectionListCard" v-for="(item, index) in favorites" :key="index">
					<div class="CollectionListCard-leftArea">
						<a href="" class="CollectionListCard-title">{{ item.title }}</a>
						<div class="CollectionListCard-creator">
							<span class="UserLink CollectionListCard-creatorAvatar">
								<div class="popover">
									<div class="popover-creatoricon">
										<a href="" class="UserLink-link">
											<img :src="item.creatorAvatar" alt="" class="avatar">
										</a>
									</div>
								</div>
							</span>
							<span class="CollectionListCard-creatorName">{{ item.creatorName }}</span>
							<span class="CollectionListCard-creatorSuffix">创建</span>
						</div>
						<div class="CollectionListCard-related">
							<span class="CollectionListCard-followersCount">{{ item.followers }} 人关注</span>
						</div>
					</div>
					<div class="CollectionListCard-rightArea">
						<div class="CollectionListCard-sampleContent">
							<div class="CollectionListCard-contentItem">
								<div class="CollectionListCard-contentTitle">
									{{ item.questionTitle }}
								</div>
								<div class="CollectionListCard-contentExcerpt">
									{{ item.answerAuthorName }}：{{ item.answerContent }}
								</div>
								<div class="CollectionListCard-contentTags">
									<span class="CollectionListCard-contentTypeTag">回答</span>
									<sapn class="CollectionListCard-contentCountTag">{{ item.voteupCount }} 赞同</sapn>
									<sapn class="CollectionListCard-contentCountTag">· {{ item.commentCount }} 评论</sapn>
								</div>
							</div>
						</div>
						<a class="CollectionListCard-entry">
							已收藏 {{ item.totalCount }} 条内容
						</a>
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
				favorites: []
			};
		},
		created() {
			this.axios.get('http://localhost:8080/api/favorite').then(res => {
				console.log(res);
				this.favorites = res.data.data;
			});
		}
	};
</script>

<style lang="scss" scoped>
	.CollectionHotListPage {
		display: block;

		.CollectionHotListPage-header {
			background: #fff;
			box-shadow: 0 1px 3px 0 rgba(26, 26, 26, .1);
			.CollectionHotListPage-title {
				margin-left: 12px;
				font-size: 25px;
				font-weight: 600;
			}
		}

		.CollectionHotListPage-header>div {
			display: flex;
			align-items: center;
			margin: 0 auto;
			width: 1000px;
			height: 100px;
		}

		.CollectionHotListPage-body {
			width: 1000px;
			margin: 10px auto 0;

			.CollectionListCard {
				display: flex;
				padding: 24px;
				width: 1000px;
				height: 179px;
				box-sizing: border-box;
				background-color: #fff;
				box-shadow: 0 1px 3px 0 rgba(26, 26, 26, .1);

				.CollectionListCard-leftArea {
					width: 270px;
					height: 131px;

					.CollectionListCard-title {
						display: block;
						height: 24px;
						line-height: 24px;
						font-size: 16px;
						overflow: hidden;
						text-overflow: ellipsis;
						white-space: nowrap;
						font-weight: 600;
					}

					.CollectionHotListPage-title {
						margin-left: 12px;
						font-size: 25px;
						font-weight: 600;
					}

					.CollectionListCard-creator {
						display: flex;
						-webkit-box-align: center;
						align-items: center;
						margin-top: 16px;
						height: 28px;

						.CollectionListCard-creatorAvatar {
							height: 28px;
							line-height: 28px;

							.popover {
								position: relative;
								display: inline-block;
								width: 28px;
								height: 36px;

								.popover-creatoricon {
									width: 28px;
									height: 36px;

									.avatar {
										background: #fff;
										border-radius: 2px;
										width: 28px;
										height: 28px;
									}
								}
							}
						}

						.CollectionListCard-creatorName {
							cursor: pointer;
							margin-left: 8px;
							color: #444;
							font-weight: 500;
							white-space: nowrap;
							overflow: hidden;
							text-overflow: ellipsis;
						}

						.CollectionListCard-creatorSuffix {
							line-height: 21;
							color: #999;
							font-size: 14px;
							flex-shrink: 0;
							margin-left: 4px;
						}
					}

					.CollectionListCard-related {
						margin-top: 29px;

						.CollectionListCard-followersCount {
							margin-left: 16px;
							color: #999;
							font-size: 14px;
						}
					}
				}

				.CollectionListCard-rightArea {
					-webkit-box-flex: 1;
					flex: 1 1;
					margin-left: 20px;
					padding-left: 20px;
					height: 131px;
					border-left: 1px solid #ebebeb;
					overflow: hidden;

					.CollectionListCard-sampleContent {
						.CollectionListCard-contentItem {
							.CollectionListCard-contentTitle {
								display: block;
								height: 21px;
								line-height: 21px;
								white-space: nowrap;
								overflow: hidden;
								text-overflow: ellipsis;
								font-weight: 600;
								font-synthesis: style;
							}

							.CollectionListCard-contentExcerpt {
								margin-top: 4px;
								max-height: 42px;
								line-height: 21px;
								color: #444;
								display: -webkit-box;
								text-overflow: ellipsis;
								overflow: hidden;
								-webkit-line-clamp: 2;
								-webkit-box-orient: vertical;
							}

							.CollectionListCard-contentTags {
								display: -webkit-box;
								display: -ms-flexbox;
								display: flex;
								-webkit-box-align: center;
								-ms-flex-align: center;
								align-items: center;
								margin-top: 8px;
								width: 641px;
								height: 20px;

								span {
									flex-shrink: 0;
								}

								.CollectionListCard-contentTypeTag {
									height: 20px;
									line-height: 20px;
									padding: 0 4px;
									background-color: #f6f6f6;
									color: #999;
									font-size: 12px;
									margin-right: 8px;
									border-radius: 2px;
								}

								.CollectionListCard-contentCountTag {
									height: 17px;
									line-height: 17px;
									font-size: 12px;
									color: #999;
								}
							}
						}
					}
					.CollectionListCard-entry {
						display: flex;
						-webkit-box-align: center;
						align-items: center;
						margin-top: 15px;
						height: 24px;
						font-size: 14px;
						color: #8590a6;
						font-weight: 500;
					}
				}
			}
		}
	}
</style>
