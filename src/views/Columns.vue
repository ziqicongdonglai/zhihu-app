<!-- 模板部分 HTML -->
<template>
	<div class="ColumnHome">
		<div class="ColumnPageHeader-nav">
			<div>
				<div class="ColumnPageHeader Sticky">
					<div class="ColumnPageHeader-content">
						<router-link to="/">
							<svg viewBox="0 0 200 91" class="Icon ZhihuLogo ZhihuLogo--blue Icon--logo" style="height:30px;width:64px" width="64"
							 height="30" aria-hidden="true">
								<title></title>
								<g>
									<path d="M53.29 80.035l7.32.002 2.41 8.24 13.128-8.24h15.477v-67.98H53.29v67.978zm7.79-60.598h22.756v53.22h-8.73l-8.718 5.473-1.587-5.46-3.72-.012v-53.22zM46.818 43.162h-16.35c.545-8.467.687-16.12.687-22.955h15.987s.615-7.05-2.68-6.97H16.807c1.09-4.1 2.46-8.332 4.1-12.708 0 0-7.523 0-10.085 6.74-1.06 2.78-4.128 13.48-9.592 24.41 1.84-.2 7.927-.37 11.512-6.94.66-1.84.785-2.08 1.605-4.54h9.02c0 3.28-.374 20.9-.526 22.95H6.51c-3.67 0-4.863 7.38-4.863 7.38H22.14C20.765 66.11 13.385 79.24 0 89.62c6.403 1.828 12.784-.29 15.937-3.094 0 0 7.182-6.53 11.12-21.64L43.92 85.18s2.473-8.402-.388-12.496c-2.37-2.788-8.768-10.33-11.496-13.064l-4.57 3.627c1.363-4.368 2.183-8.61 2.46-12.71H49.19s-.027-7.38-2.372-7.38zm128.752-.502c6.51-8.013 14.054-18.302 14.054-18.302s-5.827-4.625-8.556-1.27c-1.874 2.548-11.51 15.063-11.51 15.063l6.012 4.51zm-46.903-18.462c-2.814-2.577-8.096.667-8.096.667s12.35 17.2 12.85 17.953l6.08-4.29s-8.02-11.752-10.83-14.33zM199.99 46.5c-6.18 0-40.908.292-40.953.292v-31.56c1.503 0 3.882-.124 7.14-.376 12.773-.753 21.914-1.25 27.427-1.504 0 0 3.817-8.496-.185-10.45-.96-.37-7.24 1.43-7.24 1.43s-51.63 5.153-72.61 5.64c.5 2.756 2.38 5.336 4.93 6.11 4.16 1.087 7.09.53 15.36.277 7.76-.5 13.65-.76 17.66-.76v31.19h-41.71s.88 6.97 7.97 7.14h33.73v22.16c0 4.364-3.498 6.87-7.65 6.6-4.4.034-8.15-.36-13.027-.566.623 1.24 1.977 4.496 6.035 6.824 3.087 1.502 5.054 2.053 8.13 2.053 9.237 0 14.27-5.4 14.027-14.16V53.93h38.235c3.026 0 2.72-7.432 2.72-7.432z"
									 fill-rule="evenodd"></path>
								</g>
							</svg>
						</router-link>
						<div class="ColumnPageHeader-Button">
							<button type="button" class="Button ColumnPageHeader-WriteButton Button--blue"><svg class="Zi Zi--EditSurround"
								 fill="currentColor" viewBox="0 0 24 24" width="24" height="24">
									<path d="M18.453 7.992l-1.833-1.65.964-.978a1.223 1.223 0 0 1 1.73-.012l.005.006a1.24 1.24 0 0 1 .007 1.748l-.873.886zm-1.178 1.194l-5.578 5.66-1.935.697a.393.393 0 0 1-.504-.504l.697-1.935 5.488-5.567 1.832 1.65zM7.58 5.848l5.654.006-1.539 1.991-3.666.012A1.02 1.02 0 0 0 7 8.868v7.993c0 .558.46 1.01 1.029 1.01l7.941-.01c.568 0 1.03-.453 1.03-1.012v-4.061l2-1.442v6.002c0 1.397-1.2 2.501-2.62 2.501H7.574C6.153 19.85 5 18.717 5 17.32V8.35c0-1.397 1.16-2.502 2.58-2.502z"></path>
								</svg>写文章</button>
						</div>
					</div>
				</div>
			</div>
		</div>
		<div class="ColumnHomeTop">

		</div>
		<div class="ColumnHomeRecommendation">
			<h3 class="ColumnHomeTitle">
				<div class="ColumnHomeTitle-text">
					专栏 · 发现
				</div>
				<!-- <div class="ColumnHomeTitle-line"></div> -->
			</h3>
			<div class="ColumnHomeRecommendation-cardContainer">
				<a :href="item.url" class="ColumnHomeColumnCard ColumnHomeRecommendation-card" target="_blank" v-for="(item, index) in columns" :key="index">
					<img :src="item.imageUrl" alt="" class="Avatar Avatar--medium Avatar--round ColumnHomeColumnCard-Avatar" width="48"
					 height="48">
					<div class="ColumnHomeColumnCard-info">
						<div class="ColumnHomeColumnCard-title">
							{{ item.title }}
						</div>
						<div class="ColumnHomeColumnCard-description">
							{{ item.description }}
						</div>
					</div>
					<div class="ColumnHomeColumnCard-meta">{{ item.followers }} 人关注 | {{ item.articlesCount }} 篇文章
					</div>
					<button type="button" class="Button ColumnHomeColumnCard-followButton Button--green">进入专栏</button>
				</a>
			</div>
			<button type="button" class="Button ColumnHomeRecommendation-refreshButton Button--grey Button--withIcon Button--withLabel"><span
				 style="display:inline-flex;align-items:center">​<svg class="Zi Zi--Refresh Button-zi" fill="currentColor" viewBox="0 0 24 24"
					 width="1.2em" height="1.2em">
						<path d="M20 12.878C20 17.358 16.411 21 12 21s-8-3.643-8-8.122c0-4.044 3.032-7.51 6.954-8.038.034-1.185.012-1.049.012-1.049-.013-.728.461-1.003 1.057-.615l3.311 2.158c.598.39.596 1.026 0 1.418l-3.31 2.181c-.598.393-1.08.12-1.079-.606 0 0 .006-.606-.003-1.157-2.689.51-4.675 2.9-4.675 5.708 0 3.21 2.572 5.822 5.733 5.822 3.163 0 5.733-2.612 5.733-5.822 0-.633.51-1.148 1.134-1.148.625 0 1.133.515 1.133 1.148"
						 fill-rule="evenodd"></path>
					</svg></span>换一换</button>
		</div>
		<div class="ColumnHomeButtom ColumnHome-HomeButtom">

		</div>
	</div>
</template>

<!-- JS部分 -->
<script>
	export default {
		name: 'columns',
		data() {
			return {
				columns: []
			};
		},
		created() {
			this.axios.get('http://localhost:8080/api/columns/').then(res => {
				console.log(res);
				this.columns = res.data.data;
			});
		}
	};
</script>

<!-- 样式部分 -->
<style lang="scss" scoped>
	.ColumnHome {
		display: block;

		.ColumnPageHeader-nav {
			width: 100%;

			.ColumnPageHeader {
				position: relative;
				width: 100%;
				height: 52px;
				background: #fff;
				background-clip: content-box;
				box-shadow: 0 1px 3px rgba(26, 26, 26, .1);

				.ColumnPageHeader-content {
					display: flex;
					height: 52px;
					-webkit-box-align: center;
					align-items: center;
					position: relative;
					width: 1000px;
					padding: 0 16px;
					margin: 0 auto;

					.ZhihuLogo {
						fill: #0084ff;
					}

					.ColumnPageHeader-Button {
						-webkit-box-flex: 1;
						-ms-flex: 1 1;
						flex: 1 1;
						-webkit-box-pack: end;
						-ms-flex-pack: end;
						justify-content: flex-end;
						display: -webkit-box;
						display: -ms-flexbox;
						display: flex;
						-webkit-box-align: center;
						-ms-flex-align: center;
						align-items: center;

						.ColumnPageHeader-WriteButton {
							display: -webkit-box;
							display: -ms-flexbox;
							display: flex;
							-webkit-box-align: center;
							-ms-flex-align: center;
							align-items: center;


							.Zi--EditSurround {
								margin-left: -7px;
								margin-bottom: 2px;
							}
						}

						.Button--blue {
							color: #0084ff;
							border-color: #0084ff;
						}

					}
				}
			}
		}

		.ColumnHomeRecommendation {
			width: 666px;
			-webkit-box-align: center;
			-ms-flex-align: center;
			align-items: center;
			display: -webkit-box;
			display: -ms-flexbox;
			display: flex;
			-webkit-box-orient: vertical;
			-webkit-box-direction: normal;
			-ms-flex-direction: column;
			flex-direction: column;
			margin: 48px auto 0;
			width: 888px;

			.ColumnHomeTitle {
				-webkit-box-align: center;
				-ms-flex-align: center;
				align-items: center;
				display: -webkit-box;
				display: -ms-flexbox;
				display: flex;
				-webkit-box-pack: center;
				-ms-flex-pack: center;
				justify-content: center;
				margin: 0 3px 32px;
				width: 666px;
				height: 21.6px;

				.ColumnHomeTitle-text {
					color: #1a1a1a;
					font-size: 14px;
					line-height: 22;
					margin: 0 16px;
					font-weight: 600;
				}

				.ColumnHomeTitle-line {
					display: block;
					background: #d3d3d3;
					display: none;
					-webkit-box-flex: 1;
					-ms-flex-positive: 1;
					flex-grow: 1;
					height: 1px;
				}
			}

			.ColumnHomeRecommendation-cardContainer {
				display: flex;
				flex-wrap: wrap;

				.ColumnHomeRecommendation-card {
					margin: 0 8px 16px;
				}

				.ColumnHomeColumnCard {
					-webkit-box-align: center;
					-ms-flex-align: center;
					align-items: center;
					background: #fff;
					border-radius: 4px;
					-webkit-box-shadow: 0 8px 18px rgba(0, 0, 0, .06);
					box-shadow: 0 8px 18px rgba(0, 0, 0, .06);
					-webkit-box-sizing: border-box;
					box-sizing: border-box;
					display: -webkit-box;
					display: -ms-flexbox;
					display: flex;
					-webkit-box-orient: vertical;
					-webkit-box-direction: normal;
					-ms-flex-direction: column;
					flex-direction: column;
					padding: 26px 0 23px;
					width: 206px;

					.Avatar--round {
						border-radius: 50%;
					}

					.Avatar--medium {
						border-radius: 3px;
					}

					.Avatar {
						background: #fff;
						border-radius: 2px;
					}

					.ColumnHomeColumnCard-info {
						-webkit-box-align: center;
						-ms-flex-align: center;
						align-items: center;
						display: -webkit-box;
						display: -ms-flexbox;
						display: flex;
						-webkit-box-orient: vertical;
						-webkit-box-direction: normal;
						-ms-flex-direction: column;
						flex-direction: column;
						-webkit-box-flex: 1;
						-ms-flex-positive: 1;
						flex-grow: 1;
						padding: 0 16px;

						.ColumnHomeColumnCard-title {
							margin-top: 16px;
							display: -webkit-box;
							text-overflow: ellipsis;
							overflow: hidden;
							-webkit-line-clamp: 1;
							-webkit-box-orient: vertical;
							font-weight: 600;
						}

						.ColumnHomeColumnCard-description {
							color: grey;
							font-size: 14px;
							line-height: 21px;
							margin-top: 7px;
							text-align: center;
							word-break: break-all;
							display: -webkit-box;
							text-overflow: ellipsis;
							overflow: hidden;
							-webkit-line-clamp: 2;
							-webkit-box-orient: vertical;
						}
					}
					.ColumnHomeColumnCard-meta {
						color: grey;
						font-size: 14px;
						margin-top: 14px;
					}
					.ColumnHomeColumnCard-followButton {
					    margin-top: 15px;
					    -ms-flex-negative: 0;
					    flex-shrink: 0;
					}
					.Button--green {
					    color: #11a668;
					    border-color: #11a668;
					}
				}
			}
			.ColumnHomeRecommendation-refreshButton {
			    border-color: #444;
			    color: #444;
			    margin-top: 20px;
			    width: 98px;
			}
			.Button--grey {
			    color: #8590a6;
			    border-color: #8590a6;
			}
		}
	}
</style>
