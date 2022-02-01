<template lang="pug">
	b-modal(id="edit-product" hide-footer hide-header-close hide-header)
		b-container.bv-example-row.mt-3 Editar artículo
		b-form-row
			b-form-input.mt-3(:placeholder="productEdited.nombre" required v-model="productEdited.nombre")
			b-input-group.mt-3(prepend="$" append=".00")
				b-form-input(type="number" :placeholder="productEdited.precio" required v-model="productEdited.precio")
			b-file.mb-2.mt-3(plain required v-model="productEdited.imagen")
			p.mt-3 Vista previa del producto:
			b-card.w-50
				b-card-text {{ productEdited.img ? productEdited.img.name : '' }}
				b-card-text {{ productEdited.name }}
				b-card-text ${{ productEdited.price }}
			b-col.d-flex.flex-row-reverse.my-2.gap-3
				b-button(variant="primary" @click="$bvModal.hide('edit-product'), editProduct(productEdited)") Actualizar
				b-button(variant="secondary" @click="$bvModal.hide('edit-product')") Cancelar
</template>
<script>
import axios from 'axios'
import Swal from 'sweetalert2'

export default {
	data(){
		return {
			productos: [],
			productEdited: {},
		}
	},
	methods: {
		editProduct( {nombre, precio, imagen, id} ){
			const url = 'http://localhost:5000/api/'
			axios.put(url + id, {
				nombre, precio, imagen, id
			}).then(res => {
				Swal.fire('Producto modificado con éxito', '', 'success')
				.then(res => { window.location.reload() }) 
			}).catch(err => {
				console.log(err);
			})
		},
	}
}
</script>