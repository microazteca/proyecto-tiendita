<template lang="pug">
b-container.mt-3
  b-row
    b-col.mb-3(cols="6" sm="4" md="3" v-for="product in products" :key="product.id")
      b-card.h-100
        b-card-img(:src='product.image').image.mb-2
        b-card-text {{ product.name }}
        b-card-text ${{ product.price }}
        template(#footer)
          b-col.d-flex.my-2.justify-content-around
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
      const products = await fetch(process.env.ENDPOINT, {
        method: 'GET',
      })
      const productsJson = await products.json()
      this.products = productsJson
    },
    editProduct({ product, formulario }) {
      const { id } = product
      const url = process.env.ENDPOINT
      const formData = new FormData(formulario)
      axios
        .put(url + id, formData, {
          headers: { 'Content-Type': 'multipart/form-data' },
        })
        .then((res) => {
          Swal.fire('Producto modificado con éxito', '', 'success').then(
            (res) => {
              window.location.reload()
            }
          )
        })
        .catch((res, err) => {
          res.send(err)
        })
    },
    openEditModal(id) {
      const [newProduct] = this.products.filter((product) => product.id === id)
      this.productEdited = JSON.parse(JSON.stringify(newProduct))
    },
    deleteProduct(id) {
      const url = process.env.ENDPOINT
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
.image {
  height: 150px;
  object-fit: contain;
}

.icon {
  color: var(--static-white);
  width: 20px;
}
</style>
