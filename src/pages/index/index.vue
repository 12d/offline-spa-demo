<style lang="less" scoped>
	.login-msg {
		padding: 50px;
		text-align: center;
	}
	.msg {
		padding: 50px;
		text-align: center;
		font-size: 20px;
		color: red;
	}
</style>
<template>
	<div>
		<v-header title="首页">
			<router-link slot="right" v-if="user.id" to="/home">{{user.name}}</router-link>
		</v-header>
		<div class="login-msg" v-if="!user.id">
			<button type="button" @click="goLogin">你还未登录，请先登录</button>
		</div>
		<div class="msg" v-if="user.id">
			<img width="50" :src="logo" alt=""> <br>
			哈哈，恭喜你已经入坑Vue2
		</div>
	</div>
</template>
<script>
    import { mapState } from 'vuex';
		import aladdin from '../../common/aladdin';

	import logo from './logo.png'
    export default {
		methods: {
			goLogin(){
				console.log('gologin');
				aladdin.navigator.forward({
					url: 'http://lv.me:3000/login',
					title: '登录'
				});
			}
		},
		data() {
			return {
				logo
			}
		},
        computed: mapState({ user: state => state.user }),
    }
</script>
