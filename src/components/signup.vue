<template>
	<form>
		<div class="form-group">
			<label for="username">Username</label>
			<input 
				type="text" 
				name="username" 
				id="username" 
				class="form-control"
				v-model="username">
		</div>
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
		<button class="btn btn-primary" @click.prevent="signup">Sign Up</button>
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
			signup() {
				axios.post('http://penktas.app/api/user',
					{name: this.username, email: this.email, password: this.password},
					{headers: {'X-Requested-With':'XMLHttpRequest'}})
					.then(
						(response) => console.log(response)
					)
					.catch(
						(error) => console.log(error)
					);
			}
		}
	}
</script>