<template>
	<view class="content">
		<!-- <view class="zhutou"> -->
			<!-- <view class="zhutou_nei" style="background-color: #007AFF; border-radius: 10rpx;"><text class="zhutou_ziti">使用记录</text></view> -->
			<!-- <view class="zhutou_nei" style="background-color: #F0AD4E;"><text class="zhutou_ziti">待使用</text></view>
			<view class="zhutou_nei" style="background-color: #4CD964;"><text class="zhutou_ziti">已使用</text></view>
			<view class="zhutou_nei" style="background-color: #007AFF;"><text class="zhutou_ziti">查询</text></view>
			<view class="zhutou_nei" style="background-color: #DD524D; border-bottom-right-radius:10rpx;border-top-right-radius: 10rpx;"><text class="zhutou_ziti">无效</text></view> -->
		<!-- </view> -->
		
		<view class="neirong_b">
			<view class="zhu_xingxi">
				<view class="jibenxingxi"><text class="zhutou_ziti">券码记录</text></view>				
				<view class="biaotou">
					<text class="id">序列号</text>
					<text class="quanma">券码</text>
					<text class="shangchuan_time">上传时间</text>
					<text class="zhuangtai">状态</text>
				</view>
				
				<view class="shuju" v-for="item,index in zhuangtai" :key="index">
					<view class="id_n"><text>{{item.id}}</text></view>
					<view class="quanma_n"><text class="quanma_m">{{item.kami}}</text></view>
					<view class="shangchuan_time_n"><text class="quanma_m">{{item.date_a}}</text></view>
					<view class="jiage">
					<text class="quanma_c">{{item.state==1?'未审核':item.state==2?'无效':item.state==3?'已收录':item.state==4?'已打款':''}}</text>
				</view>												
				</view>
				
			</view>			
		</view>		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				zhuangtai:[
					{id:'',kami:'',date_a:'',state:''},
					{id:'',kami:'',date_a:'',state:''},
				]
			}
			
		},
		onShow() {
			var that=this;
			uni.request({
			    url: 'https://lsfxcx.gzybty.cn/public/index.php/index/index/get_quan',
			    data:{},
				method:'post',
			    header: {
			       'content-type': 'application/x-www-form-urlencoded'
			    },
			    success: (res) => {
			        console.log('sfs',res.data.quan);
					
						that.zhuangtai=res.data.quan;												
						if(res.data.code=='1'){
					 	uni.showToast({
					 		title:'返回数据失败！',
					 		icon:'none'
					 	})				
					 }
					
						}

			})
		},
		methods: {
			
		}
	}
</script>

<style>
.content{
	width: 100%;
	height: 100%;
}
.zhutou{
	width: 90vw;
	height: 50rpx;
	margin-top: 40rpx;
	margin-bottom: 40rpx;
	margin-left: 25rpx;
	display: flex;
	flex-direction: row;
}
.zhutou_nei{
	width: 90vw;
	height: 50rpx;
	text-align: center;
	
}
.zhutou_ziti{
	color: #FFFFFF;
	font-size: 25rpx;
	line-height: 50rpx;
}
.neirong_b{
	padding-left: 5vw;
}
.jibenxingxi{
	width: 90vw;
	height: 50rpx;
	background-color: #007AFF;
	text-align: center;
	margin-bottom: 30rpx;
}
.zhu_xingxi{
	width: 90vw;
	height: 100%;
	border: #007AFF 2rpx solid;
	margin-top: 7vw;
	
}
.zhutou_ziti{
	color: #FFFFFF;
	font-size: 25rpx;
	line-height: 50rpx;
}
.biaotou{
	width: 87vw;
	height: 100%; 
	border-bottom: #999999 1rpx solid;
	padding-left: 2vw;
}
.quanma{
	font-size: 25rpx;
	margin-right: 23vw;
}
.shangchuan_time{
	font-size: 25rpx;
	margin-right: 17vw;
}
.id{
	width: 10vw;
	font-size: 25rpx;
	margin-right: 10vw;
}
.shuju{
	margin-top: 5vw;
	margin-bottom: 5vw;
	display: flex;
	flex-direction: row;
	width: 90vw;
	height: 50rpx;
}
.quanma_n{
	margin: 0vw 2vw;
	width: 40vw;	
	overflow: auto;
}
.id_n{
	font-size: 25rpx; 
	margin: 0 5vw;
	line-height: 50rpx;
}
.quanma_m{
	font-size: 25rpx; 
}
.shangchuan_time_n{
	width: 30vw;
	padding-left: 3vw;
	margin-right: 5vw;
}
.jiage{
	width: 20vw;
	font-size: 25rpx; 
	padding-left: 0vw;
}
.zhuangtai{
	font-size: 25rpx;
	/* width: ; */
}
</style>
