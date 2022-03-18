<template lang="pug">
	.products
		h2.title Productos
		.searchBar
			i.searchBar__i
				IconSearch.searchBar__icon
			input.searchBar__input(type="text" v-model="searchBar" placeholder="¿Qué estás buscando?")
		.grid
			Card(v-for="product in filteredProducts" :key="product.id")
				slot(slot="img")
					.img-container
						img(:src="product.image")
				slot(slot="producto") {{ product.name }}
				slot(slot="precio") ${{ product.price }}
</template>
<script>
export default {
  data() {
    return {
      searchBar: '',
      products: [],
    }
  },
  computed: {
    filteredProducts() {
      return this.products.filter((product) =>
        product.name.toLowerCase().includes(this.searchBar.toLowerCase())
      )
    },
  },
  mounted() {
    this.getProducts()
  },
  methods: {
    async getProducts() {
      const products = await fetch(process.env.ENDPOINT, {
        method: 'GET',
      })
      const productsJson = await products.json()
      this.products = productsJson
    }
  },
}
</script>

<style lang="scss" scoped>
.products {
  display: flex;
  flex-direction: column;
  margin: 10px 10px 50px;

  @media (min-width: 1024px){
    margin: 10px 50px 50px;
  }
}

.title {
  color: var(--text-black);
  font-size: 26px;
  margin-bottom: 5px;

  @media (min-width: 1024px) {
    text-align: center;
    margin-bottom: 10px;
  }
}

.searchBar {
  display: flex;
  margin: 0 10px;
  position: relative;
  justify-content: flex-end;
  align-items: center;

  @media (min-width: 1024px) {
    margin: 0 auto 10px;
  }

  &__input {
    background-color: var(--static-primary-300);
    border-radius: 19px;
    border: solid 1px var(--static-grey-600);
    padding: 5px 10px;
    width: 100%;
    color: var(--static-white);

    &::placeholder{
      color: var(--static-white);
    }

    @media (min-width: 1024px) {
      width: 680px;
    }
  }

  &__i{
    position: absolute;
    margin: 0 12px;
  }

  &__icon {
    width: 18px;
    color: var(--static-white);
  }
}

.grid {
  margin-top: 13px;
  width: 100%;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 18px;
  padding: 0 10px;

  @media (min-width: 768px) {
    grid-template-columns: repeat(4, 1fr);
  }

  @media (min-width: 1024px) {
    grid-template-columns: repeat(6, 1fr);
  }
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
