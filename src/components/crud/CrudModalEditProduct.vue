<template lang="pug">
	b-modal(id="modalEditProduct" hide-footer hide-header-close hide-header)
		b-container.bv-example-row.mt-3 Editar artículo
		b-form-row
			b-form-input.mt-3(:placeholder="product.name" required v-model="product.name")
			b-input-group.mt-3(prepend="$")
				b-form-input(type="number" :placeholder="product.price" required v-model="product.price")
			b-file.mb-2.mt-3(plain required)
			p.mt-3 Vista previa del producto:
			b-card.w-50
				b-card-text {{ product.image }}
				b-card-text {{ product.name }}
				b-card-text ${{ product.price }}
			b-col.d-flex.flex-row-reverse.my-2.gap-3
				b-button(variant="primary" @click="$bvModal.hide('modalEditProduct'), $emit('editProduct', product)") Actualizar
				b-button(variant="secondary" @click="$bvModal.hide('modalEditProduct')") Cancelar
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
