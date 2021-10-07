<template>	
	<view class="content" >		
		<view class="zhu_nei">
			<!-- <view class="touxiang_kuang"> -->
				<!-- <view class="touxiang">
					<image src="" class="touxiang_image" mode=""></image>
				</view> -->
				<!-- <view class="qianMing" style="margin-top: 40rpx;"><text class="qianMing_z">灯火阑珊，如同坠落的星光。————夏蝉摘星</text></view> -->
			<!-- </view> -->
			<view class="neirong_a">
				<text class="xunyu">佳晖代理券码</text>
				<br/>
				<!-- <text class="chaxun" @click="chaxun">查询数据<text style="color: #007AFF;">://jinshuju.net/f/R9aOoL/s/4x1OVB</text></text>
				<view class="xian"></view> -->
				
				<!-- <text class="hongseziti">售后标记</text>
				<br/>
				<view class="houtaisujutianxie"><text class="huiseziti">后台数据填写，代理不要勾选</text></view>
				<br/>
				<radio-group @change="cunzai">
				<view class="shouhoukuang" style="margin-bottom: 30rpx;"><radio :value="shouhou" :checked="check"  @click="qufan()"></radio><text class="hongsezitixiao">存在售后</text></view>
				</radio-group> -->
				<!-- <text class="hongseziti">时间</text>
				<br/>
				<view class="houtaisujutianxie"><text class="huiseziti">完成结算时会更新时间到表格</text></view>
				<input type="data" class="kuang" placeholder="1970/1/1" placeholder-class="placeholder" v-model="date" > -->
				
				<!-- <text class="hongseziti">*&nbsp代理微信昵称</text>
				<input type="text" class="kuang" v-model="nicheng" style="margin-top: 10rpx;">
				<text class="hongsezitichaoxiao" style="position: relative;top: -30rpx;">请填写此项</text> -->
				
				<view style="margin-bottom: 10rpx;"><text class="hongseziti" >*&nbsp类型&nbsp&nbsp（谨慎选择，选错返撸）</text></view>

				<text class="huiseziti">临期卷码不要提交，小窗佳晖处理</text>
				<radio-group @change="radioChange">
				<view class="shouhoukuang" v-for='(item,index) in quan_data' :key="index"><radio :value="item.quan_ma"></radio><text class="hongsezitixiao">{{item.quan_ma}}</text></view>
				</radio-group>
				
			<!-- 	<view style="margin-top: 30rpx;"><text class="hongseziti">*&nbsp数量</text></view>
				<input type="text" class="kuang" v-model="shuliang" style="margin-top: 10rpx;"> -->
				<view class="hongseziti" style="margin-top: 30rpx;">*&nbsp数量</view>
				<!-- <text class="huiseziti">采用:&nbsp手机号+查询密匙<text style="color: #DD524D;">二者全对</text>才能查询，建议密匙<text style="color: #DD524D;">不要太简单</text>对自己的安全负责方法为范围分为范围分为</text> -->
				<input type="text" class="kuang" v-model="mishi"/>
				
				<view style="margin-top: 30rpx;"><text class="hongseziti">*&nbsp兑换码/卡密</text><br/></view>
				<text class="hongsezitichaoxiao" style="">合并示范</text>
				<view>	<text class="huiseziti">1896001803024333</text><br/></view>
				<view><text class="huiseziti">1896001850546000</text></view>
				<textarea maxlength="6000" cols="20" rows="2" v-model="kami" style="width: 80vw;margin: 0 3vw;" ></textarea>
				
			<!-- 	<view class="hongseziti" style="margin-top: 30rpx;">*&nbsp数量</view>
				<input type="text" class="kuang" v-model="mishi"/>
				 -->
				<view class="hongseziti" style="margin-top: 30rpx;">备注</view>
				<input type="text" v-model="beizhu" class="kuang" style="margin-top: 10rpx;">
				
				<view class="hongseziti">*&nbsp微信号（方便找到你）</view>
				<input type="text" v-model="nicheng" class="kuang" style="margin-top: 10rpx;"/>
				

				
				<view class="xian"></view>
				
				
				<button class="tijiao_btn" @click="tijiao">提交</button>
				
				
			</view>
			
			
		</view>
		
		<view class="beizhu"><text class="beizhu_text">提交即授权该表单收集您的填写信息</text></view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
			//	shouhou:'',
			//	date:'',
				nicheng:'',
				shuliang:'',
				kami:'',
				beizhu:'',
				//phone:'',
				mishi:'',
				check:false,
				radio:'',
			quan_data:[
				{id:"", quan_ma:""},
				{id:"", quan_ma:""}
				
			]
			} 
		},
		onLoad() {
			var that=this;
			uni.request({
			    url: 'https://lsfxcx.gzybty.cn/public/index.php/index/index/get_index_quan',
			    data: {},
				method:'post',
			    header: {
			       'content-type': 'application/x-www-form-urlencoded'
			    },
			    success: (res) => {
			        console.log('s',res.data);
					if(res.data.code=='2'){
						uni.showToast({
							title:'卡券返回失败'
						})
					}else{
						console.log('wo',res.data)
						that.quan_data=res.data.index_quan;
						
						
					}
			       
			    }
			})
		}, 
		methods: {
			// chaxun:function(){
			// 	uni.navigateTo({
			// 		url:'https://jinshuju.net/f/R9aOoL/s/4x1OVB'
			// 	})
			// },
			qufan:function(e){
				this.check = !this.check;
			},
			cunzai:function(evt){
				this.shouhou=evt.detail.value;				
			}, 
			radioChange:function(e){
				this.radio=e.detail.value;		
			},
			tijiao:function(){		
				// if(this.check==true){
				// 	this.shouhou=="存在售后"
				// }else{
				// 	this.shouhou==""
				// }			
				// if(date==""){
				// 	uni.showModal({
				// 		content:'请输入时间。'
				// 	})
				// 	}else 
				// if(nicheng==""){
				// 		uni.showToast({
				// 			content:'请输入微信昵称。'
				// 		})
				// 		}else 
				var that=this;
				var phone_reg=/^[1][3,4,5,7,8,9][0-9]{9}$/;
				// if(this.shuliang==''){
				// 		uni.showToast({
				// 			content:'请输入要出售的数量。',
				// 			icon:"none"
				// 		})
				// 		}else 
						if(this.radio==''){
						uni.showToast({
							title:'请选择卡券类型。',
							icon:"none"
						})
						}else if(this.kami==''){
						uni.showToast({
							title:'请输入卡券号码。',
							icon:"none"
						})
						}
						else if(this.mishi==''){
						uni.showToast({
							title:'请输入卡券数量。',
							icon:"none"
						})
						}else if(this.nicheng==''){ 
						uni.showToast({
							title:'请输入微信号。',
							icon:"none"
						})
						// else if(!(phone_reg.test(this.phone))){ 
						// uni.showToast({
						// 	title:'请输正确手机号码。',
						// 	icon:"none"
						// })
						}
						else{					
					uni.request({ 
					    url: 'https://lsfxcx.gzybty.cn/public/index.php/index/index/addform',
					    data: {
					        // shouhou:this.shouhou,			
					        // date:this.data,			
					        // nicheng:this.nicheng,	
							radio:that.radio,
					        // shuliang:that.shuliang,	
							nicheng:that.nicheng,
					        kami:that.kami,			
					        beizhu:that.beizhu,			
					        //phone:that.phone,				
					        mishi:that.mishi, 
					    },
						method:'post',
					    header: {
					       'content-type': 'application/x-www-form-urlencoded'
					    },
					    success: (res) => {
					        console.log('li',res.data);
							
							
							if(res.data.code=='3'){
								uni.showToast({
									title:'更新券成功'
								})
							
							}
							else if(res.data.code=='1'){
								uni.showModal({								
									title:"提交成功",
									content:that.radio + '数量：'+that.mishi+'  序列号；'+res.data.id,	
									showCancel:false,
									success: function (res) {
									        if (res.confirm) {
												that.kami="";
												that.mishi="";
									         uni.switchTab({
									         	url:'../quanma_manage/quanma_manage'
									         })
									        } else if (res.cancel) {
									            
									        }
									    }
								})																					 								
							}else if(res.data.code=='2'){
								uni.showToast({
									title:'您的券码已被其他人提交过',
									icon:'none'
								})
							}else if(res.data.code=='4'){
								uni.showToast({
									title:'数据库内有相同数据请勿重复提交',
									icon:'none'
								})
							}
					       
					    }
					})
				
					}
				},
				
			}

		
	}
</script>

<style>
page{
	background-color: #A1BBE4;
	width: 100%;
	height: 100%;
}
.content{
	width: 100vw;
	height: 100%;
}
.placeholder{
	color: #C8C7CC;
	margin-left: 20rpx;
	letter-spacing: 2rpx;
}
view,text{
	word-wrap: break-word;
	word-break: break-all;
	white-space: pre-line;
}
.zhu_nei{
	width:90vw;
	margin:10vw 5vw;
	padding: 5vw 0;
	background-color: #FFFFFF;
}
.touxiang_kuang{
	/* margin: 0 5vw; */
	width: 90vw;
	height: 100rpx;
	background-image: url(../../static/touxiangkuang.png);
	margin-bottom: 30rpx;
}
.touxiang{
	margin-top: 20rpx;
	margin-bottom: 20rpx;
	margin-left: 30rpx;
	width: 60rpx;
	height: 60rpx;
	display: inline-block;
}
.touxiang_image{

	width: 60rpx;
	height: 60rpx;
	border-radius: 50%;
	background-color: #FFFFFF;
}
.qianMing{
	display: inline-block;
}
.qianMing_z{
	font-size: 26rpx;
	color: white;
	margin-left: 20rpx;
}
.neirong_a{
	width:100%;
	
	height: 100%;
	background-color: #FFFFFF;
}
.xunyu{
	font-family: 宋体;
	font-size: 38rpx;
	margin-left: 20rpx;
}
.chaxun{
	font-size: 18rpx;
	margin-top: 10rpx;
	margin-left: 20rpx;
}
.xian{
	margin-top: 30rpx;
	margin-bottom: 30rpx;
	background-color: #C0C0C0;
	width: 100vw;
	height: 2rpx;
}
.hongseziti{ 
	font-size: 30rpx;
	font-family: 黑体;
	color: #DD524D;
	margin-left: 20rpx;
}
.houtaisujutianxie{
	margin-top:10rpx ;
	margin-bottom: 10rpx;
}
.huiseziti{
	margin-left: 20rpx;
	font-size: 24rpx;
	color: #C0C0C0;
	
}
.hongsezitixiao{
	margin-left: 20rpx;
	font-size: 24rpx;
	color: #DD524D;
	line-height: 40rpx;
}
.shouhoukuang{
	border: 1rpx solid #C0C0C0;
	width: 80vw;
	padding:1vw 1vw ;
	margin: 0 3vw;
	overflow: hidden;
}
/* radio{
	margin-left: 10rpx;
} */
.kuang{
	border: 1rpx solid #C0C0C0;
	width: 80vw;
	/* height: 40rpx; */
	margin: 0 3vw;
	margin-bottom: 30rpx;
	padding-left: 10rpx;
}
textarea{
	border: 1rpx solid #C0C0C0;
	margin-left: 20rpx;
	width: 650rpx;
	height: 100rpx;
}
.hongsezitichaoxiao{
	font-size: 22rpx;
	margin-left: 20rpx;
	color: #ff8787;
}
.tijiao_btn{
	width: 80vw;
	/* padding: 1vh 0; */
	background-color: #DD524D;
	margin-bottom: 5vw;
	font-size: 28rpx;
	color: #FFFFFF;
}
.tijiao_text{
	font-size: 25rpx;
	color: #FFFFFF;
	line-height: 55rpx;

}
/* .jubao_btn{
	float: right;
	margin-right: 25rpx;
	margin-bottom: 35rpx;
} */
/* .jubao_text{
	position: relative;
	top: -35rpx;
	font-size: 18rpx;
	color: #C8C7CC;
} */
.beizhu{
	width:100vw;
	margin-bottom: 20vw;

	text-align: center;
}
.beizhu_text{
	color: #FFFFFF;
	/* box-shadow: 10px 10px 10px #333333; */
}
</style>
