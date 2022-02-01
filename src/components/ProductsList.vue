<template lang="pug">
	b-container.bv-example-row.mt-3.d-flex.gap-3
		b-card(v-for="producto in productos" :key="producto.id").w-50
			b-card-img(:src="producto.img")
			b-card-text {{ producto.nombre }}
			b-card-text {{ producto.precio }}
			b-col.d-flex.my-2.gap-2
				b-button.py-1.px-2(variant="dark" @click="$bvModal.show('edit-product'), openEditModal(producto.id)")
					IconEdit.icon
				b-button.py-1.px-2(variant="danger" @click="deleteProduct(producto.id)")
					IconDelete.icon
</template>
<script>
import axios from 'axios'
import Swal from 'sweetalert2'

export default {
	data(){
		return {
			productos: [],
			productEdited: {}
		}
	},
	mounted(){
		this.getProducts();
	},
	methods: {
		async getProducts(){
			const products = await fetch('http://localhost:5000/api', {method: 'GET'})
			const productsJson = await products.json()
			this.productos = productsJson
		},
		openEditModal(id){
			const [newProduct] = this.productos.filter(producto => producto.id === id)
			this.productEdited = JSON.parse(JSON.stringify(newProduct))
		},
		deleteProduct(id){
			const url = 'http://localhost:5000/api/'
			Swal.fire({
				title: '¿Confirma la eliminación del producto?',
				confirmButtonText: 'Confirmar',
				showCancelButton: true,
				cancelButtonText: 'Cancelar'
			}).then((result) => {
				if(result.isConfirmed){
					axios.delete(url + id).then(response => {
						Swal.fire('Producto eliminado con éxito', '', 'success')
						.then(res => { window.location.reload() })
					})
				}
			})
		}
	}
}
</script>
<style lang="scss" scoped>
	.icon{
		color: var(--static-white);
		width: 20px;
	}
</style>