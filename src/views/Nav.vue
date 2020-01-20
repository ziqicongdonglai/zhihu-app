<template>
	<div>
		<div class="nav gutter">
			<div class="nav-bar">
				<div class="link-logo"></div>
				<div class="top-search">
					<form action="">
						<label for="q" class="hide-text">知乎搜索</label>
						<input type="text" class="top-search-input" name="q" autocomplete="off" placeholder="搜索你感兴趣的内容..."/>
						<button type="submit" class="top-search-button" value="搜索"></button>
					</form>
				</div>
				<ul class="nav-list flex-left">
					<li class="nav-item">
						<router-link to="/home">首页</router-link>
					</li>
					<li class="nav-item">
						<router-link to="/explore">发现</router-link>
					</li>
					<li class="nav-item">
						<router-link to="/question/waiting">等你来答</router-link>
					</li>
					<li class="nav-item abs-center-right">
						<router-link to="/login">登录</router-link>
					</li>
				</ul>
			</div>
		</div>
		<!-- 二级路由入口 -->
		<router-view />
	</div>
</template>

<script>
export default {
	name: 'nav',
	data() {
		return {};
	},
	created() {}
};
</script>

<style lang="scss" scoped>
// .main {
// 	text-align: center;
// }
// .main {
// 	height: 2300px;
// }
.router-link-active {
	border-bottom: 2px solid #fff;
}
.gutter {
	position: relative;
	margin-bottom: 10px;
}
.nav-bar {
	height: 45px;
	background: linear-gradient(to bottom,#086ed5,#055db5);
	padding-left: 300px;
	// text-align: center;
	.link-logo {
		float: left;
		width: 61px;
		height: 100%;
		background-image: url(https://static.zhihu.com/static/revved/img/sticky_header/new_logo.ede2316d.png);
		background-repeat: no-repeat;
		background-position: 0 8px;
		color: #fff;
	}
	.top-search {
		float: left;
		margin: 7px 0 0 12px;
		.hide-text {
		    font: 0/0 a;
		    color: transparent;
		    text-shadow: none;
		    background-color: transparent;
		    border: 0;
		}
		.top-search-input {
		    padding: 7px 50px 7px 10px;
		    width: 100%;
		    color: #49525c;
		    font-size: 14px;
		    line-height: 17px;
		    background-color: #e1eaf2;
		    border: 1px solid #045bb2;
		    border-radius: 4px;
		    box-shadow: inset 0 1px 3px rgba(0,0,0,.2), 0 1px 0 rgba(255,255,255,.1);
		    outline: 0;
		    box-sizing: border-box;
		    -webkit-transition: all .2s ease-in-out;
		    transition: all .2s ease-in-out;
		}
	}
	.nav-list {
		height: 45px;
		.nav-item {
			float: left;
			width: 65px;
			height: 45px;
			line-height: 45px;
			font-size: 14px;
			padding-right: 10px;
			text-align: center;
			// box-sizing: border-box;
			a {
				color: #eee;
			}
		}
	}
}

</style>
