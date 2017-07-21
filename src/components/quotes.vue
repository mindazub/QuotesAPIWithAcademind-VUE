<template>
	<div>
		<button 
			class="btn btn-primary"
			@click="onGetQuotes"
		>
			Get Quotes
		</button>
		<hr>
		<app-quote v-for="quote in quotes" :qt="quote" @quoteDeleted="onQuoteDeleted($event)"></app-quote>
	</div>
</template>

<script>
	import Quote from './quote.vue';
	import axios from 'axios';

	export default {
		data() {
			return {
				quotes: []
			}
		},
		
		methods: {
			onGetQuotes() {
				axios.get('http://penktas.app/api/quotes')
					.then(
						response => [
							this.quotes = response.data.quotes,
						]
					)
					.catch(
						error => console.log(error),
					);
			},
			onQuoteDeleted(id) {
				const postition = this.quotes.findIndex((element) =>{
					return element.id == id;
				});
				this.quotes.splice(postition, 1);
			}
		},
		components: {
			'app-quote': Quote
		}
}

</script>