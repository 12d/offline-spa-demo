<style lang="less" scoped>
	.login {
		padding: 50px;
		text-align: center;
		.line {
			padding: 5px;
			input {
				padding: 0 10px;
				line-height: 28px;
			}
		}
		button {
			padding: 0 20px;
			margin-top: 20px;
			line-height: 28px;
		}
	}
</style>
<template>
	<div>
		<v-header title="登录">
			<router-link slot="left" to="/">返回</router-link>
		</v-header>
		<div class="login">
			<div class="line">
				<div v-show="btn && !form.id">id不能为空</div>
				<input type="number" placeholder="输入你的id" v-model="form.id">
			</div>
			<div class="line">
				<div v-show="btn && !form.name">用户名不能为空</div>
				<input type="text" placeholder="输入你的用户名" v-model="form.name">
			</div>
			<button  type="button" @click="goSubmit">登录</button>
			<button  type="button" v-on:click="a">登录2</button>
		</div>
	</div>
</template>
<script>
    import { mapActions } from 'vuex'
    import { USER_SIGNIN } from 'store/user'
		import aladdin from '../../common/aladdin';
    export default {
        data() {
			return {
				btn: false, //true 已经提交过， false没有提交过
				form: {
					id: '',
					name: ''
				}
			}
		},
		methods: {
			a(){alert(112)},
			goSubmit() {
				alert(1)
				this.btn = true
				if(!this.form.id || !this.form.name) return
				this.USER_SIGNIN(this.form)
				//this.$router.replace({ path: '/home' })
				aladdin.navigator.forward({
					url: 'http://lv.me:3000/home',
					title: '个人首页'
				});
			}
		}
    }
</script>
