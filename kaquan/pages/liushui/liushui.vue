<template>
	<view class="content"> 
		<view class="zhutou">
			<view class="zhutou_nei" style="background-color: #007AFF; border-bottom-left-radius:10rpx;border-top-left-radius: 10rpx;" @click="tiaozhuana"><text class="zhutou_ziti">提现申请</text></view>
			<view class="zhutou_nei" style="background-color: #F0AD4E;" @tap="tiaozhuanb"><text class="zhutou_ziti">待处理</text></view>
			<view class="zhutou_nei" style="background-color: #4CD964;"><text class="zhutou_ziti">成功</text></view>
			<view class="zhutou_nei" style="background-color: #DD524D; border-bottom-right-radius:10rpx;border-top-right-radius: 10rpx;"><text class="zhutou_ziti">失败</text></view>
		</view>
		
		<view class="neirong_b">
			<view class="zhu_xingxi" v-if="tiaozhuan==='1'">
				<view class="jibenxingxi"><text class="zhutou_ziti">提现申请</text></view>
				
				<view class="zhu_xingming">
					<view class="xingming"><text class="huiseziti">可提金额:</text></view>
					<view class="input"><input type="text" v-model="keti" :placeholder="jine"></view>
				</view>
				<view class="zhu_xingming">
					<view class="xingming"><text class="hongseziti">申请金额:</text></view>
					<view class="input"><input type="number" v-model="shenqing"></view>
				</view>
				<view class="zhu_xingming">
					<view class="xingming"><text class="huiseziti">备注:</text></view>
					<view class="input"><input type="text" v-model="beizhu"></view>
				</view>
							
				<view class="tijiao"><text class="zhutou_ziti" @click="tijiao">提交</text></view>
			</view>
			
		</view>
		
		
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				tiaozhuan:'1',
				keti:'',
				shenqing:'',
				beizhu:'',
				jine:'0.0'
			}
		},
		methods: {
			tiaozhuanb:function(){
				 this.tiaozhuan=2;
				console.log('tiaozhuan',this.tiaozhuan);
				uni.navigateTo({
					url:'../index/index'
				})
			},
			tijiao:function(){
				var keti=this.keti;
				var shenqing=this.shenqing;
				var beizhu=this.beizhu;
				var jine=this.jine;
			}
		}
	}
</script>

<style>
.content{
	width: 100%;
	height: 100%;
}
.zhutou{
	width: 700rpx;
	height: 50rpx;
	margin-top: 40rpx;
	margin-bottom: 40rpx;
	margin-left: 25rpx;
	display: flex;
	flex-direction: row;
	border-radius:0  10rpx  0 10rpx;
}
.zhutou_nei{
	width: 175rpx;
	height: 50rpx;
	text-align: center;
	
}
.zhutou_ziti{
	color: #FFFFFF;
	font-size: 25rpx;
	line-height: 50rpx;
}
.hongseziti{
	font-size: 25rpx;
	color: #DD524D;
	line-height: 60rpx;
}
.xingming{
	margin-left: 30rpx;
	border-top-left-radius: 5rpx;
	border-bottom-left-radius: 5rpx;
	height: 60rpx;
	width: 180rpx;
	background-color: #e6e6e6;
	text-align: center;
}
input{
	width: 420rpx;
	height: 57rpx;
	border: #C8C7CC 2rpx solid;
	padding-left: 20rpx;
}
.zhu_xingxi{
	width: 700rpx;
	height: 300rpx;
	border: #007AFF 2rpx solid;
	
}
.neirong_b{
	padding-left: 25rpx;
}
.jibenxingxi{
	width: 700rpx;
	height: 50rpx;
	background-color: #007AFF;
	text-align: center;
	margin-bottom: 30rpx;
}
.zhutou_ziti{
	color: #FFFFFF;
	font-size: 25rpx;
	line-height: 50rpx;
}
.zhu_xingming{
	display: flex;
	flex-direction: row;
}
.huiseziti{
	font-size: 25rpx;
	color: #333333;
	line-height: 60rpx;
}
.tijiao{
	width: 700rpx;
	height: 50rpx;
	background-color: #007AFF;
	text-align: center;
	margin-top:70rpx;
}
</style>
