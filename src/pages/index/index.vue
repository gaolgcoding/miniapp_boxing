<template>
	<view class="content">
		<view class="banner">
			<image class="logo" src="/static/images/logo.jpg"></image>
			<image class="background-pic" src="/static/images/gym.jpg"></image>
			<text class="name">BOXING HALL拳馆</text>
			<text class="text">一家专业拳馆</text>
			<view v-if="textFolded" class="text">
				<text>适合所有想要提升自己、寻求进步、增强自...</text>
				<text class="fold-btn" @click="toggleTextFold">展开</text>
			</view>
			<view v-else class="text">
				<text>适合所有想要提升自己、寻求进步、增强自信的人。公主病或王子病患者、只想嘻哈玩闹、消磨时间的，请绕路。</text>
				<text class="fold-btn" @click="toggleTextFold">收起</text>
			</view>
		</view>
		<view class="gps">
			<view class="gps-box">
				<uni-icons type="location" size="20" color="green"></uni-icons>
				<text>广东省深圳市福田区劲松大厦11C</text>
			</view>
			<view class="gps-box">|<uni-icons type="phone" size="20" color="green"></uni-icons></view>
		</view>
		<view class="team">
			<text>教练团队</text>
			<view class="coach-box">
				<view
					v-for="(coach, key) in coaches"
					:key="key"
					class="coach-item"
				>
					<image class="coach-image" :src="coach.url"></image>
					<text class="coach-name">{{coach.name}}</text>
					<text class="coach-profile">{{coach.profile}}</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			textFolded: true,
			coaches: [
				{
					name: 'SLAVA斯拉瓦',
					profile: '俄罗斯拳击教练，7年半职业生涯，打过80余场专业拳击比赛，自2011年从业教练至今....',
					url: 'https://p0.meituan.net/dpmerchantpic/475e11c9ed1d5038b073500f4525dbd71026817.jpg'
				},
				{
					name: 'BRUNO布鲁诺',
					profile: '巴西本土黑带柔术教练。柔术训练生涯达十年，参加过...',
					url: 'https://p1.itc.cn/q_70/images03/20201226/f8c19a3390d949bf9520d5240ecf541b.jpeg'
				},
				{
					name: 'VIVIAN西米鹿',
					profile: '有氧拳击教练。私教教学风格耐心细致，能帮助...',
					url: 'https://pic1.zhimg.com/v2-d0e06b26e7f17630970b0860bb0b0b00_r.jpg'
				},
				{
					name: 'ARTEM阿特姆',
					profile: '自由搏击教练',
					url: 'https://www.eastern-club.com/Uploads/202103/603c9296a5952.jpg'
				},
				{
					name: 'BRIAN王春来',
					profile: 'BOXING HALL拳馆核心成员，人谦逊温和，教学幽默风趣...',
					url: 'https://img1.baidu.com/it/u=1903655801,1221700369&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=750'
				}
			]
		}
	},
	methods: {
		toggleTextFold() {
			this.textFolded = !this.textFolded
		}
	},
	onShow() {
		const userInfo = uni.getStorageSync('userInfo')
		if (!userInfo) {
			uni.navigateTo({
				url: '/pages/login/index'
			})
		}
	}
}
</script>

<style scoped lang="less">
.content {
	height: 100vh;
	background-color: #1d1b1b;
	color: #fff;
	.banner {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		position: relative;
		height: 40vh;
		.logo {
			border-radius: 50%;
			height: 200rpx;
			width: 200rpx;
			position: relative;
		}
		.background-pic {
			position: absolute;
			width: 100%;
			height: 100%;
			z-index: 0;
			opacity: 0.1;
		}
		.name {
			margin: 20rpx 0;
		}
		.fold-btn {
			color: yellow;
			margin-left: 10rpx;
		}
		.text {
			z-index: 10;
			width: 85%;
		}
	}
	.gps {
		display: flex;
		justify-content: space-between;
		padding: 30rpx 20rpx;
		background-color: #151313;
	}
	.team {
		margin-top: 20rpx;
		background-color: #151313;
		padding: 30rpx 20rpx;
		.coach-box {
			width: 100%;
			display: flex;
			overflow: scroll;
		}
		.coach-item {
			display: inline-flex;
			flex-direction: column;
			align-items: center;
			justify-content: center;
			width: 250rpx;
			background-color: #2f2d2d;
			border-radius: 10rpx;
			padding: 10rpx;
			margin-top: 20rpx;
			margin-right: 10rpx;
			.coach-image {
				display: block;
				width: 200rpx;
				height: 200rpx;
				border-radius: 50%;
			}
			.coach-profile {
				font-size: 26rpx;
				color: gray;
				overflow: hidden;
				text-overflow: ellipsis;
				display: -webkit-box;
				-webkit-line-clamp: 2;
				overflow:hidden;
				-webkit-box-orient: vertical;
			}
		}
	}
}
</style>
