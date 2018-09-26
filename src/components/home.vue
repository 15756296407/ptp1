<template>
    <div>
        <div class="banner">
			<div class="banner-bk">
				<div class="nav">
					<img class="imgg" src="../assets/images/logo2018.png" alt="">
					<ul class="lists">
						<li><span>币种行情</span></li>
						<li><span>币种行情</span></li>
						<li><span>币种行情</span></li>
						<li><span>币种行情</span></li>
						<li><span>币种行情</span></li>
						<li><span>币种行情</span></li>
						<li><span>币种行情</span></li>
						<li><span>币种行情</span></li>
					</ul>
				</div>
				<div class="video">
					<a href="javascript:void(0)">
						<img src="../assets/images/banner_tech_tilil.png" alt="">
					</a>
				</div>
			</div>
        </div>
    </div>
</template>


<style lang="less" scoped>
.banner {
	background: url(../assets/images/h-banner-bg.png) repeat 0 0;
	width: 100%;
	height: 600px;
	position:relative;
	.banner-bk{
		width:100%;
		height:100%;
		background: url(../assets/images/homebanner-techbk.png) no-repeat center center;
		.nav{
			width:980px;
			height: 80px;
			padding: 43px 15px 0;
			display: flex;
			align-items: center;
			justify-content: space-between;
			.imgg{
				width: 209px;
				height: 47px;
			}
			.lists{
				display: flex;
				align-items: center;
				color:#fff;
				li{
					padding: 0 10px;
				}
			}
		}
		.video{
			height:240px;
			img{
				width:480px;
				margin-top:10px;
			}
		}
	}
}
</style>
