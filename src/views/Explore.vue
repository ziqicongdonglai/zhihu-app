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
					<div class="explore-roundtableCard-headerBackgrounds"><img :src="item.banner" alt=""/> </div>
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
	</div>
</template>

<script>
	export default {
		name: 'explore',
		data() {
			return {
				specials: [],
				roundtables: []
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
	}
};
</script>

<style lang="scss" scoped>
	h3 {
		text-align: left;
	}
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
				box-shadow: 0 1px 3px 0 rgba(26,26,26,.1);
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
				    box-shadow: rgba(26,26,26,.1);
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
