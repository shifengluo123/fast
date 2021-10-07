<template>
	<view class="content">
		<view class="neirong_c">
			<view class="kuang" v-for="item,index in item" :key="index"><text class="ziti">{{item.neirong}}</text></view>
			
			
		</view>
		
		
		
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				item:[
					{name:'星巴克',neirong:'【星巴克|饮品券代金券星礼卡等】'},
					{name:'必胜客',neirong:'【必胜客|代金券星礼卡等】'},
					{name:'肯德基',neirong:'【星巴克|代金券星礼卡蛋挞等】'},
					{name:'饮品券',neirong:'【瑞幸|喜茶|奈雪的茶】'},
					{name:'百果园',neirong:'【百果园各面值代金券】'},
				]
			}
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
.neirong_c{
	margin-top: 25rpx;
	margin-left: 35rpx;
	width: 680rpx;
	height: 1334rpx;
	border: #C0C0C0 2rpx solid;
	border-radius: 5rpx;
}
.kuang{
	width: 660rpx;
	height: 60rpx;
	border-bottom: #C0C0C0 2rpx solid;
	padding-left: 20rpx;
}
.ziti{
	font-size: 25rpx;
	line-height: 60rpx;
	font-family: 宋体;
}
</style>
