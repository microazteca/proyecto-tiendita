<template lang="pug">
	b-modal(id="edit-product" hide-footer hide-header-close hide-header)
		b-container.bv-example-row.mt-3 Editar artículo
		b-form-row
			b-form-input.mt-3(:placeholder="product.nombre" required v-model="product.nombre")
			b-input-group.mt-3(prepend="$")
				b-form-input(type="number" :placeholder="product.precio" required v-model="product.precio")
			b-file.mb-2.mt-3(plain required)
			p.mt-3 Vista previa del producto:
			b-card.w-50
				b-card-text {{ product.imagen }}
				b-card-text {{ product.nombre }}
				b-card-text ${{ product.precio }}
			b-col.d-flex.flex-row-reverse.my-2.gap-3
				b-button(variant="primary" @click="$bvModal.hide('edit-product'), $emit('editProduct', product)") Actualizar
				b-button(variant="secondary" @click="$bvModal.hide('edit-product')") Cancelar
</template>
<script>
export default {
  props: {
    product: {
      type: Object,
      default() {
        return {}
      },
    },
  },
}
</script>
