<template lang="pug">
div
	b-container.bv-example-row.mt-3.d-flex.gap-3
		b-card(v-for="product in products" :key="product.id").w-50
			b-card-img(:src="product.image")
			b-card-text {{ product.name }}
			b-card-text {{ product.price }}
			b-col.d-flex.my-2.gap-2
				b-button.py-1.px-2(variant="dark" @click="$bvModal.show('modalEditProduct'), openEditModal(product.id)")
					IconEdit.icon
				b-button.py-1.px-2(variant="danger" @click="deleteProduct(product.id)")
					IconDelete.icon
	CrudModalEditProduct(:product="productEdited" @editProduct="editProduct")
</template>
<script>
import axios from 'axios'
import Swal from 'sweetalert2'

export default {
  data() {
    return {
      products: [],
      productEdited: {},
    }
  },
  mounted() {
    this.getProducts()
  },
  methods: {
    async getProducts() {
      const products = await fetch('http://localhost:5000/api', {
        method: 'GET',
      })
      const productsJson = await products.json()
      this.products = productsJson
    },
    editProduct(product) {
      const { name, image, price, id } = product
      const url = 'http://localhost:5000/api/'
      axios
        .put(url + id, {
          name,
          price,
          image,
          id,
        })
        .then((res) => {
          Swal.fire('Producto modificado con éxito', '', 'success').then(
            (res) => {
              window.location.reload()
            }
          )
        })
        .catch((err) => {
          console.log(err)
        })
    },
    openEditModal(id) {
      const [newProduct] = this.products.filter((product) => product.id === id)
      this.productEdited = JSON.parse(JSON.stringify(newProduct))
    },
    deleteProduct(id) {
      const url = 'http://localhost:5000/api/'
      Swal.fire({
        title: '¿Confirma la eliminación del producto?',
        confirmButtonText: 'Confirmar',
        showCancelButton: true,
        cancelButtonText: 'Cancelar',
      }).then((result) => {
        if (result.isConfirmed) {
          axios.delete(url + id).then((response) => {
            Swal.fire('Producto eliminado con éxito', '', 'success').then(
              (res) => {
                window.location.reload()
              }
            )
          })
        }
      })
    },
  },
}
</script>
<style lang="scss" scoped>
.icon {
  color: var(--static-white);
  width: 20px;
}
</style>
