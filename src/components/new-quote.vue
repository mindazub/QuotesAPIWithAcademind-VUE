<template>
	<form @submit.prevent="onSubmitted">
		<div class="form-group">
			<label for="content">Content</label>
			<input 
				type="text" 
				id="content" 
				class="form-control" 
				v-model="quoteContent"
			>
		</div>
		<button class="btn btn-primary">Submit</button>
	</form>
</template>

<script>
	export default {
		data() {
			return {
				quoteContent: ''
			}
		},
		methods: {
			onSubmitted() {
				
			}
		}
	}
</script>