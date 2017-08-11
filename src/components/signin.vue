<template>
	<form>
		<div class="form-group">
			<label for="email">Email</label>
			<input 
				type="email" 
				name="email" 
				id="email" 
				class="form-control"
				v-model="email">
		</div>
			<label for="password">Password</label>
			<input 
				type="password" 
				name="password" 
				id="password" 
				class="form-control"
				v-model="password">
		</div>
		<button class="btn btn-primary" @click.prevent="signin">Sign In</button>
	</form>
</template>

<script>
	import axios from 'axios';
	
	export default {
		data(){
			return {
				username: '',
				email: '',
				password: ''
			}
		},
		methods: {
			signin() {
				axios.post('http://penktas.app/api/user/signin',
					{email: this.email, password: this.password},
					{headers: {'X-Requested-With':'XMLHttpRequest'}})
					.then(
						(response) => {
							const token = response.data.token;
							const base64Url = token.split('.')[1];
							const base64 = base64Url.replace('-', '+').replace('_', '/');
							console.log(JSON.parse(window.atob(base64)));
							localStorage.setItem('token', token);
						}
					)
					.catch(
						(error) => console.log(error)
					);
			}
		}
	}
</script>