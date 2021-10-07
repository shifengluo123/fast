<template>
	<view class="content">
		<view class="zhutou">
			<view class="zhutou_nei" @tap="tiaozhuan_a" style="background-color: #007AFF; border-bottom-left-radius:10rpx;border-top-left-radius: 10rpx;"><text class="zhutou_ziti">个人信息</text></view>
			<!-- <view class="zhutou_nei" @tap="tiaozhuan_b" style="background-color: #F0AD4E;"><text class="zhutou_ziti">卖券数</text></view> -->
			<view class="zhutou_nei" style="background-color: #4CD964;" @tap="tiaozhuan_c"><text class="zhutou_ziti">收款项</text></view>
			<!-- <view class="zhutou_nei" style="background-color: #DD524D; border-bottom-right-radius:10rpx;border-top-right-radius: 10rpx;"><text class="zhutou_ziti">信用分</text></view> -->
		</view>
		
		<view class="neirong_b" v-if="tiaozhuan=='1'">
			<view class="zhu_xingxi">
				<view class="jibenxingxi"><text class="zhutou_ziti">基本信息</text></view>
				
				<view class="zhu_xingming">
					<view class="xingming"><text class="hongseziti">姓名:</text></view>
					<view class="input"><input type="text"  v-model="xingxi.name" ></view>
				</view>	
				<view class="zhu_xingming">
					<view class="xingming"><text class="hongseziti">手机号:</text></view>
					<view class="input"><input type="number" v-model="xingxi.phone" ></view>
				</view>
				<view class="zhu_xingming">
					<view class="xingming"><text class="hongseziti">微信:</text></view>
					<view class="input"><input type="text" v-model="xingxi.weChat" ></view>
				</view>
				<view class="zhu_xingming">
					<view class="xingming"><text class="hongseziti">QQ:</text></view>
					<view class="input"><input type="number" v-model="xingxi.qq"></view>
				</view>
				<view class="zhu_xingming">
					<view class="xingming"><text class="hongseziti">邮箱:</text></view>
					<view class="input"><input type="email" v-model="xingxi.email"></view>
				</view>
				
				
				<view class="zhu_shoukuan">
					<view class="shoukuanxingxi"><text class="zhutou_ziti">收款信息</text></view>
					<view class="zhu_xingming">
						<view class="zhenshi" ><text class="huiseziti" >真实姓名:</text></view>
						<view  ><input type="text" class="input_b" v-model="xingxi.true_name"></view>
					</view>
					<view class="zhu_xingming">
						<view class="zhenshi"><text class="huiseziti">支付宝账号:</text></view>
						<view ><input type="text" class="input_b" v-model="xingxi.alipay"></view>
					</view>
					
				</view> 
				
				<view class="baocun" @tap="baocun()"><text class="zhutou_ziti" >保存</text></view>
			</view>
						
		</view>
		
		<view class="neirong_b" v-if="tiaozhuan=='2'">
			<view class="zhu_xingxi" style="height:100%; border-color:#b4ff8a;">
				<view class="jibenxingxi" style="background-color: #b4ff8a;"><text class="zhutou_ziti" style="color: #4CD964;">纪录</text></view>
				
				<view class="zhu_xingming">
					<view class="xingming"><text class="hongseziti" style="color: #333333;">已打款笔数:</text></view>
					<view class="input"><text class="hongseziti" style="color: #333333;">{{yidakuan}}</text></view>
				</view>
				<view class="zhu_xingming">
					<view class="xingming"><text class="hongseziti" style="color: #333333;">未处理笔数:</text></view>
					<view class="input"><text class="hongseziti" style="color: #333333;">{{weichuli}}</text></view>
				</view>
<!-- 				<view class="zhu_xingming">
					<view class="xingming"><text class="hongseziti" style="color: #333333;">成功笔数:</text></view>
					<view class="input"><input type="text" v-model="success_n"></view>
				</view>
				<view class="zhu_xingming">
					<view class="xingming"><text class="hongseziti" style="color: #333333;">成功金额:</text></view>
					<view class="input"><input type="number" v-model="success_m"></view>
				</view> -->
<!-- 				<view class="zhu_xingming">
					<view class="xingming"><text class="hongseziti" style="color: #333333;">失败笔数:</text></view>
					<view class="input"><input type="email" v-model="fail_n"></view>
				</view>
				<view class="zhu_xingming">
					<view class="xingming"><text class="hongseziti" style="color: #333333;">失败金额:</text></view>
					<view class="input"><input type="number" v-model="fail_m"></view>
				</view> -->
				<view class="zhu_xingming">
					<view class="xingming"><text class="hongseziti" style="color: #333333;">合计:</text></view>
					<view class="input"><text class="hongseziti" style="color: #333333;">{{yidakuan+weichuli}}</text></view>
				</view>
		</view>
		</view>
		 
		<!-- <view class="neirong_b" v-if="tiaozhuan=='3'">
			<view class="zhu_xingxi" style="height:350rpx; border-color:#fffac7;">
				<view class="jibenxingxi" style="background-color: #fffac7;"><text class="zhutou_ziti" style="color: #F0AD4E;">卖券数</text></view>
				
				<view class="zhu_xingming">
					<view class="xingming"><text class="hongseziti" style="color: #333333;">待处理:</text></view>
					<view class="input"><input type="text" v-model="daichuli"></view>
				</view>
				<view class="zhu_xingming">
					<view class="xingming"><text class="hongseziti" style="color: #333333;">待使用:</text></view>
					<view class="input"><input type="number" v-model="daishiyong"></view>
				</view>
				<view class="zhu_xingming">
					<view class="xingming"><text class="hongseziti" style="color: #333333;">已使用:</text></view>
					<view class="input"><input type="text" v-model="yishiyong"></view>
				</view>
				<view class="zhu_xingming">
					<view class="xingming"><text class="hongseziti" style="color: #333333;">无效:</text></view>
					<view class="input"><input type="number" v-model="wuxiao"></view>
				</view>
				<view class="zhu_xingming">
					<view class="xingming"><text class="hongseziti" style="color: #333333;">合计:</text></view>
					<view class="input"><input type="email" v-model="quan_all"></view>
				</view>
		</view>
		</view> -->
		
		
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				xingxi:
					{
					name:'',
					phone:'',
					weChat:'',
					qq:'',
					email:'',
					true_name:'',
					alipay:'',
					
					}
				,
				tiaozhuan:'1',
							
					yidakuan:'',
					weichuli:'',
				//	heji:'',
				
				// success_n:'',
				// success_m:'',
				// fail_n:'',
				// fail_m:'',
				// all:'',
				
				// daichuli:'',
				// daishiyong:'',
				// yishiyong:'',
				// wuxiao:'',
				// quan_all:''
			}
		},
		onShow() {
			var that=this;
			uni.request({
			    url: 'https://lsfxcx.gzybty.cn/public/index.php/index/index/chaxun_state',
			    data:{},
				method:'post',
			    header: {
			       'content-type': 'application/x-www-form-urlencoded'
			    },
			    success: (res) => {
			        console.log('a_count',res.data.a_count);
					if(res.data.code=='1'){
						that.yidakuan = res.data.a_count;
						that.weichuli = res.data.b_count;
					}     
			    }
			})
		},
		onLoad() {
			var that=this;
			console.log("xingxi",this.xingxi)
			uni.request({
			    url: 'https://lsfxcx.gzybty.cn/public/index.php/index/index/chaxun_jiben',
			    data:{},
				method:'post',
			    header: {
			       'content-type': 'application/x-www-form-urlencoded'
			    },
			    success: (res) => {
			        console.log('data',res.data);
					if(res.data.code=='1'){
						that.xingxi=res.data.data;
					}     
			    }
			})
		},
		methods: {
			baocun:function(){		
				// var that=this;
				var xingxi=this.xingxi;
				console.log('123',xingxi);
				//return false;
				var reg = /^([a-zA-Z]|[0-9])(\w|\-)+@[a-zA-Z0-9]+\.([a-zA-Z]{2,4})$/;
				var phone_reg=/^[1][3,4,5,7,8,9][0-9]{9}$/;
				console.log("phone_reg",phone_reg.test(xingxi.phone)+'|'+xingxi.phone);
				if(xingxi.name==''){
					uni.showToast({
						title:'请输入姓名！',
						icon:'none'
					})
				}else if(!(phone_reg.test(xingxi.phone))){
					uni.showToast({
						title:'请输入正确的手机号！',
						icon:'none'
					})
				}else if(xingxi.weChat==''){
					uni.showToast({
						title:'请输入微信名！',
						icon:'none'
					})
				}else if(!reg.test(xingxi.email)){
					uni.showToast({
						title:'请输入正确的邮箱格式！',
						icon:'none'
					})
				}else if(xingxi.true_name==''){
					uni.showToast({
						title:'请输入真实姓名！',
						icon:'none'
					})
				}else if(xingxi.alipay==''){
					uni.showToast({
						title:'请输入支付宝账号！',
						icon:'none'
					})
				}else{
					uni.request({
					    url: 'https://lsfxcx.gzybty.cn/public/index.php/index/index/xingxi',
					    data:xingxi,
						method:'post',
					    header: {
					       'content-type': 'application/x-www-form-urlencoded'
					    },
					    success: (res) => {
					        console.log('s',res.data);
							if(res.data.code=='1'){
								uni.showToast({
									title:'保存成功'
								})
							}else{
								uni.showToast({
									title:'请不要重复提交',
									icon:'none'
								})
							}
					       
					    }
					})
				}
				

			},
			tiaozhuan_c:function(){
				this.tiaozhuan=2;
			},
			// tiaozhuan_b:function(){
			// 	this.tiaozhuan=3;
			// },
			
			tiaozhuan_a:function(){
				this.tiaozhuan=1;
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
	width: 90vw;
	height: 50rpx;
	margin: 5vw;
	display: flex;
	flex-direction: row;
	border-radius:0  10rpx  0 10rpx;
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
	padding: 5vw;
}
.zhu_xingxi{
	width: 90vw;
	
	height: 350rpx;
	border: #007AFF 2rpx solid;
	
}
.jibenxingxi{
	width: 90vw;
	height: 50rpx;
	background-color: #007AFF;
	text-align: center;
	margin-bottom: 30rpx;
}
.shoukuanxingxi{
	width: 90vw;
	height: 50rpx;
	text-align: center;
	margin-bottom: 30rpx;
	background-color: #ffd6ed;
}
.zhu_xingming{
	display: flex;
	flex-direction: row;
	width: 80vw;
	margin-left: 5vw;
}

.xingming{
	margin-left: 30rpx;
	border-top-left-radius: 5rpx;
	border-bottom-left-radius: 5rpx;
	height: 50rpx;
	width: 15vw;
	background-color: #e6e6e6;
	text-align: center;
}
.zhenshi{
	margin-left: 30rpx;
	border-top-left-radius: 5rpx;
	border-bottom-left-radius: 5rpx;
	width: 180rpx;
	height: 60rpx;
	text-align: center;
	background-color: #e6e6e6;
}
.huiseziti{
	font-size: 25rpx;
	color: #333333;
	line-height: 60rpx;
}
.input_b{
	width: 420rpx;
	height: 57rpx;
	border: #C0C0C0 1rpx solid;
}
.hongseziti{
	font-size: 25rpx;
	color: #DD524D;
	line-height: 42rpx;
}
.input{
	width: 55vw;
	height: 42rpx;
	border: #C8C7CC 1rpx solid;
	padding: 3rpx 3rpx 0 15rpx;
}
input{
	width: 55vw;
	height: 42rpx;
	font-size: 25rpx;
	padding: 3rpx 0 3rpx 15rpx;
}
.zhu_shoukuan{
	width: 90vw; 
	height: 240rpx;
	border: #e6e6e6 2rpx solid;
	margin-top: 80rpx;
}
.baocun{
	width: 90vw;
	height: 50rpx;
	background-color: #007AFF;
	text-align: center;
	margin-top: 40rpx;
}
</style>
