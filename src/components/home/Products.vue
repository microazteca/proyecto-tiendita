<template lang="pug">
	.products
		h2.title Productos
		SearchBar.search-bar
		.grid
			Card(v-for="product in products" :key="product.id")
				slot(slot="img")
					.img-container
						img(:src="products.image")
				slot(slot="producto") {{ product.name }}
				slot(slot="precio") ${{ product.price }}
</template>
<script>
export default {
  data() {
    return {
      products: [],
    }
  },
  mounted() {
    this.getProducts()
  },
  methods: {
    async getProducts() {
      console.log(process.env.ENDPOINT)
      const products = await fetch(process.env.ENDPOINT, {
        method: 'GET',
      })
      const productsJson = await products.json()
      this.products = productsJson
    },
  },
}
</script>

<style lang="scss" scoped>
.products {
  display: flex;
  flex-direction: column;
  margin: 10px 10px 50px;
}

.title {
  color: var(--text-black);
  font-size: 26px;
  margin-bottom: 5px;
}

.grid {
  margin-top: 13px;
  width: 100%;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 18px;
  padding: 0 10px;
}

.img-container {
  width: 100%;
  display: flex;
  justify-content: center;
}

img {
  width: 100px;
  object-fit: cover;
}
</style>
