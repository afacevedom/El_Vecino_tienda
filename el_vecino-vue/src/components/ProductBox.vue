<template>
    <div class="column is-3">
        <div class="box">
            <figure class="image mb-3">
                <img v-bind:src="product.get_thumbnail">
                
               
            </figure>

            <h3 class="is-size-5">{{ product.name }}</h3>
            <br />
            <h3 class="is-size-8">SKU: {{ product.id }}</h3>
            <p class="is-size-6 has-text-grey">Precio: ${{ product.price }}</p>
            
            <router-link v-bind:to="product.get_absolute_url" class="button is-dark mt-4">Ver detalles</router-link>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ProductBox',
    props: {
        product: Object
    }
}
</script>

<style scoped>
  .image {
    margin-top: -1.25rem;
    margin-left: -1.25rem;
    margin-right: -1.25rem;
  }
</style>