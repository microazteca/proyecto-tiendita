<template lang="pug">
	.crud
		h1.m-3 Base de datos | Tiendita
		b-container
			b-button(pill variant="primary" @click="$bvModal.show('new-product')") +
		ModalNewProduct
		ProductsList
		ModalEditProduct
</template>
<script>
export default {
}
</script>

<style lang="scss" scoped>
	.icon{
		color: var(--static-white);
		width: 20px;
	}
</style>
