<template>
	<div class="home">

		<div class="columns is-multiline">
			<div class="column is-12">
				<h2 class="is-size-2 has-text-centered">Catálogo de Productos</h2>
			</div>

			<ProductBox
				v-for="product in latestProducts"
				v-bind:key="product.id"
				v-bind:product="product"
			/>
		</div>
	</div>
</template>

<script>
import axios from 'axios';
import ProductBox from '@/components/ProductBox';
export default {
	name: 'Home',
	data() {
		return {
			latestProducts: [],
		};
	},
	components: {
		ProductBox,
	},
	mounted() {
		this.getLatestProducts();
		document.title = 'Home | El Vecino';
	},
	methods: {
		async getLatestProducts() {
			this.$store.commit('setIsLoading', true);
			await axios
				.get('/api/v1/latest-products/')
				.then((response) => {
					this.latestProducts = response.data;
				})
				.catch((error) => {
					console.log(error);
				});
			this.$store.commit('setIsLoading', false);
		},
	},
};
</script>
