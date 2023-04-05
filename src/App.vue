<script>
	export default {
		onLaunch: async function() {
			console.log('App Launch')
			const login_res = await this.login()
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		},
		methods: {
			// uni.login获取用户code
			login() {
				return new Promise((resolve, reject) => {
					uni.login({
						provider: 'weixin',
						success: (res) => {
							resolve(res)
						},
						fail: err => {
							reject(err)
						}
					})
				})
			},
			// 用登录凭证code获取用户登录状态(openid, session_key)
			async getOpenidAndSessionKey(code) {
				// todo
				// const res = await getWechatOpenIdByCode({ code })
			},
			// 获取用户信息
			getWxInfo() {
				return new Promise((resolve, reject) => {
					uni.getUserInfo({
						provider: 'weixin',
						success: res => {
							resolve(res)
						},
						fail: err => {
							reject(err)
						}
					})
				})
			}
		}
	}
</script>

<style>
	/*每个页面公共css */
</style>
