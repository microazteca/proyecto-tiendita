<template lang="pug">
	.crud
		h1 Crud
		b-container
			b-button(pill variant="primary") +
		b-container.bv-example-row Artículo
			b-form-row
				b-form-input(placeholder="Nombre del producto")
				b-input-group(prepend="$" append=".00")
					b-form-input(type="number" placeholder="Precio")
				b-button(variant="outline-success") Cargar imagen
				b-col.d-flex.flex-row-reverse
					b-button(variant="primary") Guardar
					b-button(variant="secondary") Cancelar
		b-container.bv-example-row
			b-row
				b-col
					b-card(v-for="(producto, index) in productos" :key="index") {{ producto.nombre }}
						b-card-text {{ producto.precio }}
						b-card-text {{ producto.imagen }}
</template>
<script>
export default {
	data(){
		return {
			productos: [],
			text: '',
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
		}
	}
}
</script>
<style lang="scss" scoped>

</style>
