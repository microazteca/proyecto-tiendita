<template lang="pug">
	.crud
		h1.m-3 Base de datos | Tiendita
		b-container
			b-button(pill variant="primary" @click="openModal()") +
		b-modal(ref="new-product" hide-footer hide-header-close hide-header)
			b-container.bv-example-row.mt-3 Ingresar nuevo artículo
				b-form-row
					b-form-input.mt-3(placeholder="Nombre del producto" name="name" required v-model="name")
					b-input-group.mt-3(prepend="$" append=".00")
						b-form-input(type="number" placeholder="Precio" name="price" required v-model="price")
					b-file.mb-2.mt-3(placeholder="Seleccionar archivo" name="img" plain required v-model="img")
					p.mt-3 Vista previa del producto:
					b-card.w-50
						b-card-text {{ img ? img.name : '' }}
						b-card-text {{ name }}
						b-card-text ${{ price }}
					b-col.d-flex.flex-row-reverse.my-2.gap-3
						b-button(variant="primary" @click="addProduct()") Guardar
						b-button(variant="secondary" @click="closeModal()") Cancelar
		b-container.bv-example-row.mt-3.d-flex.gap-3
			b-card(v-for="producto in productos" :key="producto.id").w-50
				b-card-img(:src="producto.img")
				b-card-text {{ producto.nombre }}
				b-card-text {{ producto.precio }}
				b-card-text {{ producto.id }}
				b-col.d-flex.my-2.gap-2
					b-button.py-1.px-2(variant="dark" @click="openEditModal(producto.id)")
						IconEdit.icon
					b-button.py-1.px-2(variant="danger")
						IconDelete.icon
			b-modal(ref="edit-product" hide-footer hide-header-close hide-header)
				b-container.bv-example-row.mt-3 Editar artículo
				b-form-row
					b-form-input.mt-3(:placeholder="productEdited.nombre" required v-model="productEdited.nombre")
					b-input-group.mt-3(prepend="$" append=".00")
						b-form-input(type="number" :placeholder="productEdited.precio" required v-model="productEdited.precio")
					b-file.mb-2.mt-3(plain required v-model="productEdited.img")
					p.mt-3 Vista previa del producto:
					b-card.w-50
						b-card-text {{ productEdited.img ? productEdited.img.name : '' }}
						b-card-text {{ productEdited.name }}
						b-card-text ${{ productEdited.price }}
					b-col.d-flex.flex-row-reverse.my-2.gap-3
						b-button(variant="primary" @click="closeEditModal(), editProduct(productEdited)") Actualizar
						b-button(variant="secondary" @click="closeEditModal()") Cancelar
</template>
<script>
import axios from 'axios'

export default {
	data(){
		return {
			productos: [],
			productEdited: {},
			name: '',
			price: '',
			img: ''
		}
	},
	mounted(){
		this.getProducts();
	},
	methods: {
		openModal(){
			this.$refs['new-product'].show()
		},
		closeModal(){
			this.$refs['new-product'].hide()
		},
		openEditModal(id){
			this.$refs['edit-product'].show()
			const [newProduct] = this.productos.filter(producto => producto.id === id)
			this.productEdited = JSON.parse(JSON.stringify(newProduct))
			
		},
		closeEditModal(){
			this.$refs['edit-product'].hide()
		},
		async getProducts(){
			const products = await fetch('http://localhost:5000/api', {method: 'GET'})
			const productsJson = await products.json()
			this.productos = productsJson
		},
		addProduct(){
			const nombre = this.name
			const precio = this.price
			const imagen = this.img
			axios.post('http://localhost:5000/api', {
				nombre, precio, imagen
			}).then(res => {
				alert('Producto registrado correctamente')
			}).catch(err => {
				console.log(err);
			})
		},
		editProduct( {nombre, precio, imagen, id} ){
			const url = 'http://localhost:5000/api/'
			axios.put(url + id, {
				nombre, precio, imagen, id
			}).then(res => {
				alert('Producto modificado con éxito')
			}).catch(err => {
				console.log(err);
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
