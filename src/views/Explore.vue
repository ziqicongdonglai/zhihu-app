<template>
	<div class="exploreHomePage">
		<div class="exploreHomePage-section">
			<div class="exploreHomePage-content-header">
				<span>最新专题</span>
			</div>
			<div class="explore-specialCard" v-for="(item, index) in specials" :key="index">
				<div class="explore-specialCard-banner"><img :src="item.banner" alt="" /></div>
				<div class="explore-specialCard-header">
					<div class="explore-specialCard-info">
						<div class="explore-specialCard-title">
							<a>{{ item.title }}</a>
						</div>
						<div class="explore-specialCard-count">
							<span class="meta">{{ item.updated }}更新 · {{ item.viewCount }} 浏览</span>
						</div>
					</div>
				</div>
				<div class="explore-specialCard-contentList">
					<div v-for="(section, index) in item.sections" :key="index" class="explore-specialCard-item">
						<router-link to="/explore" class="explore-specialCard-contentTag">{{ section.sectionTitle }}</router-link>
					</div>
				</div>
			</div>
			<div class="exploreHomePage-content-moreButton">
				<router-link to="/special/all" target="_blank">查看更多专题</router-link>
			</div>
		</div>
		<div class="exploreHomePage-section">
			<div class="exploreHomePage-content-header">
				<span>圆桌讨论</span>
			</div>
			<div class="explore-roundtableCard" v-for="(item, index) in roundtables" :key="index">
				<div class="explore-roundtableCard-headerContainer">
					<div class="explore-roundtableCard-headerBackgrounds"><img :src="item.banner" alt="" /> </div>
					<div class="explore-roundtableCard-header">
						<h3>{{ item.name }}</h3>
						<p class="explore-specialCard-header">该圆桌被浏览 {{ item.visitsCount }} 次</p>
						<p class="introduction">{{ item.includeCount }} 位嘉宾参与</p>
					</div>
				</div>
				<div class="explore-roundtableCard-questionList">

				</div>
			</div>
			<div class="exploreHomePage-content-moreButton">
				<router-link to="/roundtable" target="_blank">查看更多圆桌</router-link>
			</div>
		</div>
		<div class="exploreHomePage-section">
			<div class="exploreHomePage-content-header">
				<span>热门收藏夹</span>
			</div>
			<div class="explore-content-body">
				<div class="explore-collections">
					<div class="explore-collectionCard" v-for="(item, index) in favorites" :key="index">
						<div class="explore-collectionCard-header">
							<div class="explore-collectionCard-info">
								<div class="explore-collectionCard-title">
									<a>{{ item.title }}</a>
								</div>
								<div class="explore-collectionCard-relatedMembers">
									<div class="explore-collectionCard-creator">
										<span class="explore-collectionCard-creatorAvatar">
											<div class="popover">
												<div class="popover-creatoricon">
													<a href="" class="UserLink-link">
														<img :src="item.creatorAvatar" alt="" class="avatar">
													</a>
												</div>
											</div>
										</span>
										<a href="" class="explore-collectionCard-creatorName">{{ item.creatorName }}</a>
										<span class="explore-collectionCard-creatorSuffix">创建</span>
									</div>
									<div class="explore-collectionCard-followers">
										{{ item.followers }} 关注
									</div>
								</div>
							</div>
						</div>
						<div class="explore-collectionCard-contentList">
							<div class="explore-collectionCard-contentItem">
								<a href="" class="explore-collectionCard-contentTitle">{{ item.questionTitle }}</a>
								<div class="explore-collectionCard-contentExcerpt">
									{{ item.answerAuthorName }}：{{ item.answerContent }}
								</div>
								<div class="explore-collectionCard-contentTags">
									<span class="explore-collectionCard-contentTypeTag">回答</span>
									<sapn class="explore-collectionCard-contentCountTag">{{ item.voteupCount }} 赞同</sapn>
									<sapn class="explore-collectionCard-contentCountTag">· {{ item.commentCount }} 评论</sapn>
								</div>
							</div>
						</div>
						<a class="explore-collectionCard-collectedContentCount">
							已收藏 {{ item.totalCount }} 条内容
						</a>
					</div>
				</div>
			</div>
			<div class="exploreHomePage-content-moreButton">
				<router-link to="/collection/hot" target="_blank">查看更多收藏夹</router-link>
			</div>
		</div>
		<div class="exploreHomePage-section">
			<div class="exploreHomePage-content-header">
				<span>专栏</span>
			</div>
			<div class="explore-content-body">
				<div class="explore-columns">
					<div class="explore-columnCard" v-for="(item, index) in columns" :key="index">
						<a :href="item.url" target="_blank" class="explore-columnCard-avatar">
							<img :src="item.imageUrl" alt="">
						</a>
						<a :href="item.url" target="_blank" class="explore-columnCard-title">
							{{ item.title }}
						</a>
						<div class="explore-columnCard-count">
							<span>
								{{ item.followers }} 关注
							</span>
							<span> · </span>
							<span>
								{{ item.articlesCount }} 文章
							</span>
						</div>
						<div class="explore-columnCard-intro">
							{{ item.description }}
						</div>
						<button class="explore-columnCard-entryButton">进入专栏</button>
					</div>
				</div>
			</div>
			<div class="exploreHomePage-content-moreButton">
				<router-link to="zhuanlan" target="_blank">查看更多专栏</router-link>
			</div>
		</div>
	</div>
</template>

<script>
	export default {
		name: 'explore',
		data() {
			return {
				specials: [],
				roundtables: [],
				favorites: [],
				columns: []
			};
		},
		created() {
			this.axios.get('http://localhost:8080/api/special/').then(res => {
				console.log(res);
				// console.log(typeof res.data.data[0].updated);
				this.specials = res.data.data;
			});
			this.axios.get('http://localhost:8080/api/roundtable/hot').then(res => {
				console.log(res);
				this.roundtables = res.data.data;
			});
			this.axios.get('http://localhost:8080/api/favorite/hot').then(res => {
				console.log(res);
				this.favorites = res.data.data;
			});
			this.axios.get('http://localhost:8080/api/columns/hot').then(res => {
				console.log(res);
				this.columns = res.data.data;
			});
		}
	};
</script>

<style lang="scss" scoped>
	.exploreHomePage {
		width: 70%;
		margin: 32px auto 107px;

		.exploreHomePage-section+.exploreHomePage-section {
			margin-top: 32px;
		}

		.exploreHomePage-section {
			display: block;
			height: 1050px;

			.exploreHomePage-content-header {
				display: flex;
				align-items: center;
				height: 36px;
				padding-left: 15px;

				span {
					font-size: 25px;
					font-weight: 600;
				}
			}

			.explore-specialCard {
				margin-bottom: 10px;
				// border: 1ox solid #d6d6d6;
				border-radius: 4px;
				height: 450px;
				width: 490px;
				float: left;
				margin: 14px;
				box-sizing: border-box;
				box-shadow: 0 1px 3px 0 rgba(26, 26, 26, 0.1);
				background: #fff;

				.explore-specialCard-banner {
					height: 200px;
					width: 100%;

					img {
						width: 100%;
						height: 100%;
						border-radius: 4px 4px 0 0;
						display: block;
					}
				}

				.explore-specialCard-header {
					display: flex;
					align-items: center;
					margin: 0 24px;
					padding: 30px 0;
					height: 110px;
					box-sizing: border-box;
					border-bottom: 1px solid #ebebeb;

					.explore-specialCard-info {
						flex: 1 1;

						.explore-specialCard-title {
							width: 330px;
							line-height: 28px;
							max-height: 56px;
							font-size: 20px;
							text-overflow: ellipsis;
							overflow: hidden;
							font-weight: 600;
						}

						.explore-specialCard-count {
							margin-top: 4px;
							height: 17px;
							line-height: 17px;
							font-size: 12px;
							color: #999;
						}
					}
				}

				.explore-specialCard-contentList {
					margin: 20px 24px;

					.explore-specialCard-item {
						display: flex;
						align-items: center;
						height: 24px;

						.explore-specialCard-contentTag {
							padding: 0 8px;
							height: 24px;
							line-height: 24px;
							font-size: 12px;
							color: #8590a6;
							background: #f6f6f6;
							border-radius: 5px;
						}
					}

					.explore-specialCard-item+.explore-specialCard-item {
						margin-top: 12px;
					}
				}
			}

			.explore-roundtableCard {
				width: 490px;
				height: 442px;
				float: left;
				margin: 14px;
				border-radius: 4px;
				background-color: #fff;
				box-shadow: 0 1px 3px 0 rgba(26, 26, 26, .1);
				overflow: hidden;

				.explore-roundtableCard-headerContainer {
					position: relative;
					width: 490px;
					height: 240px;

					.explore-roundtableCard-headerBackgrounds {
						position: absolute;
						top: 0;
						right: 0;
						bottom: 0;
						height: 240px;
						width: 240px;

						img {
							position: absolute;
							top: 0;
							right: 0;
							bottom: 0;
							left: 0;
							height: 240px;
							width: 100%;
						}
					}

					.explore-roundtableCard-header {
						position: relative;
						width: 320px;
						height: 147px;
						padding: 68px 24px 24px;
					}
				}
			}

			.explore-content-body {
				padding: 24px 0 20px;

				.explore-collections {
					display: flex;
					-webkit-box-pack: justify;
					justify-content: space-between;
					flex-wrap: wrap;
					align-content: space-between;
					height: 748px;

					.explore-collectionCard {
						width: 490px;
						height: 364px;
						border-radius: 4px;
						box-shadow: 0 1px 3px 0 rgba(26, 26, 26, .1);
						background-color: #fff;
						flex-shrink: 0;

						// margin: 14px;
						.explore-collectionCard-header {
							display: flex;
							margin: 0 24px;
							padding: 24px 0 20px;
							box-sizing: border-box;
							height: 112px;
							border-bottom: 1px solid #ebebeb;
							overflow: hidden;

							.explore-collectionCard-info {
								-webkit-box-flex: 1;
								flex: 1 1;
								overflow: hidden;

								.explore-collectionCard-title {
									display: block;
									height: 28px;
									line-height: 28px;
									font-size: 20px;
									overflow: hidden;
									text-overflow: ellipsis;
									white-space: nowrap;
									font-weight: 600;
								}

								.explore-collectionCard-relatedMembers {
									display: flex;
									-webkit-box-align: center;
									align-items: center;
									margin-top: 12px;

									.explore-collectionCard-creator {
										display: flex;
										-webkit-box-align: center;
										align-items: center;
										height: 28px;
										line-height: 27px;

										.explore-collectionCard-creatorAvatar {
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

										.explore-collectionCard-creatorName {
											margin-left: 8px;
											color: #444;
											font-weight: 500;
										}

										.explore-collectionCard-creatorSuffix {
											margin-left: 4px;
											color: #999;
											font-size: 14px;
											font-weight: 400;
										}
									}

									.explore-collectionCard-followers {
										margin-left: 12px;
										padding-left: 12px;
										height: 19px;
										line-height: 19px;
										font-size: 14px;
										color: #999;
										border-left: 2px solid #ebebeb;
									}
								}
							}
						}

						.explore-collectionCard-contentList {
							margin: 20px 24px;
							height: 164px;

							.explore-collectionCard-contentItem {
								.explore-collectionCard-contentTitle {
									display: block;
									height: 21px;
									line-height: 21px;
									white-space: nowrap;
									overflow: hidden;
									text-overflow: ellipsis;
									font-weight: 600;
									font-synthesis: style;
								}

								.explore-collectionCard-contentExcerpt {
									margin-top: 4px;
									height: 21px;
									line-height: 21px;
									color: #444;
									white-space: nowrap;
									overflow: hidden;
									text-overflow: ellipsis;
								}

								.explore-collectionCard-contentTags {
									display: -webkit-box;
									display: -ms-flexbox;
									display: flex;
									-webkit-box-align: center;
									-ms-flex-align: center;
									align-items: center;
									margin-top: 6px;
									width: 442px;
									height: 20px;

									span {
										flex-shrink: 0;
									}

									.explore-collectionCard-contentTypeTag {
										height: 20px;
										line-height: 20px;
										padding: 0 4px;
										background-color: #f6f6f6;
										color: #999;
										font-size: 12px;
										margin-right: 8px;
									}

									.explore-collectionCard-contentCountTag {
										height: 17px;
										line-height: 17px;
										font-size: 12px;
										color: #999;
									}
								}
							}
						}

						.explore-collectionCard-collectedContentCount {
							display: flex;
							-webkit-box-align: center;
							align-items: center;
							margin: 20px 24px 0;
							height: 24px;
							font-size: 14px;
							color: #8590a6;
							font-weight: 600;
						}
					}
				}
			}

			.explore-columns {
				display: flex;
				-webkit-box-pack: justify;
				justify-content: space-between;
				width: 1000px;
				height: 313px;

				.explore-columnCard {
					-webkit-box-flex: 1;
					-ms-flex: 1 1;
					flex: 1 1;
					display: -webkit-box;
					display: -ms-flexbox;
					display: flex;
					-webkit-box-orient: vertical;
					-webkit-box-direction: normal;
					-ms-flex-direction: column;
					flex-direction: column;
					-webkit-box-pack: center;
					-ms-flex-pack: center;
					justify-content: center;
					-webkit-box-align: center;
					-ms-flex-align: center;
					align-items: center;
					padding: 28px 24px;
					-webkit-box-sizing: border-box;
					box-sizing: border-box;
					min-width: 235px;
					height: 313px;
					border-radius: 4px;
					-webkit-box-shadow: 0 1px 3px 0 rgba(26, 26, 26, .1);
					box-shadow: 0 1px 3px 0 rgba(26, 26, 26, .1);
					background-color: #fff;

					.explore-columnCard-avatar {
						display: block;
						width: 80px;
						height: 80px;

						img {
							width: 100%;
							height: 100%;
							border-radius: 50%;
						}
					}

					.explore-columnCard-title {
						margin-top: 20px;
						height: 22px;
						line-height: 22px;
						font-size: 16px;
						max-width: 187px;
						white-space: nowrap;
						overflow: hidden;
						text-overflow: ellipsis;
						font-weight: 600;
					}

					.explore-columnCard-count {
						margin-top: 4px;
						height: 17px;
						line-height: 17px;
						font-size: 12px;
						color: #999;
					}

					.explore-columnCard-intro {
						margin-top: 20px;
						height: 40px;
						line-height: 20px;
						font-size: 14px;
						color: #444;
						text-align: center;
						display: -webkit-box;
						text-overflow: ellipsis;
						overflow: hidden;
						-webkit-line-clamp: 2;
						-webkit-box-orient: vertical;
					}

					.explore-columnCard-entryButton {
						margin-top: 20px;
						padding: 0 16px;
						height: 34px;
						font-size: 14px;
						color: #0084ff;
						background-color: rgba(0, 132, 255, .08);
						border-radius: 3px;
						font-weight: 600;
						border: 0;
					}
				}
			}

			.exploreHomePage-content-moreButton {
				width: 1000px;
				display: flex;
				height: 48px;
				justify-content: center;

				a {
					align-items: center;
					padding: 0 14px 0 14px;
					height: 48px;
					width: 115px;
					background-color: #fff;
					box-shadow: rgba(26, 26, 26, .1);
					border-radius: 25px;
					color: #8590a6;
					cursor: pointer;
					font-weight: 600;
					justify-content: center;
					display: flex;
				}
			}
		}

		.exploreHomePage-section+.exploreHomePage-section {
			margin-top: 32px;
		}
	}
</style>
