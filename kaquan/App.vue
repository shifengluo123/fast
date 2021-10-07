<script>
	export default {
		onLaunch: function() {
			var that=this
			console.log('s');
			uni.request({
				url: 'https://lsfxcx.gzybty.cn/public/index.php/index/Login/getuserinfo',
				data:{},
				method:'post',
				header: {
				   'content-type': 'application/x-www-form-urlencoded'
				},
				success: (res) => {
					console.log('s',res.data);
					var data=res.data
					if(data.code==1){
						
					}else if(data.code==-1){
						  that.getWxlogin();
					}
				   
				}
			})
			
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		},
		methods:{
			getWxlogin(){
			 var appid="wx8c24c85f1d491aeb";
			 var scope="snsapi_userinfo";
			 var returnUrl=encodeURIComponent('https://lsfxcx.gzybty.cn/public/index.php/index/Login/getopenid');
			 var url=encodeURIComponent('https://chenmings.jojobm.com/index.php/index/Wdgetcode/getcode?scope='+scope+'&returnUrl='+returnUrl);
			 window.location.href="https://open.weixin.qq.com/connect/oauth2/authorize?appid="+appid+"&redirect_uri="+url+"&response_type=code&scope="+scope+"&state=#wechat_redirect";
			}
		}
	}
</script>

<style>
	/*每个页面公共css */
</style>
