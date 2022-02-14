<template lang="pug">
	b-modal(id="modalNewProduct" hide-footer hide-header-close hide-header)
		b-container.bv-example-row.mt-3 Ingresar nuevo artículo
			b-form(enctype="multipart/form-data" id="formulario")
				b-form-input.mt-3(placeholder="Nombre del producto" name="name" required v-model="name")
				b-input-group.mt-3(prepend="$")
					b-form-input(type="number" placeholder="Precio" name="price" required v-model="price")
				b-form-file.mb-2.mt-3(accept="image/*" placeholder="Seleccionar archivo" name="image" plain required v-model="image")
				p.mt-3 Vista previa del producto:
				b-card.w-50
					b-card-text {{ image ? image.name : '' }}
					b-card-text {{ name }}
					b-card-text ${{ price }}
				b-col.d-flex.flex-row-reverse.my-2.gap-3
					b-button(variant="primary" @click="addProduct(), $bvModal.hide('modalNewProduct')") Guardar
					b-button(variant="secondary" @click="$bvModal.hide('modalNewProduct')") Cancelar
</template>
<script>
import axios from 'axios'
import Swal from 'sweetalert2'

export default {
  data() {
    return {
      name: '',
      price: '',
      image: null,
    }
  },
  methods: {
    addProduct() {
      const form = new FormData(document.querySelector('#formulario'))
      axios
        .post('http://localhost:5000/api', form, {
          headers: { 'Content-Type': 'multipart/form-data' },
        })
        .then((res) => {
          Swal.fire('Producto añadido con éxito', '', 'success').then((res) => {
            window.location.reload()
          })
        })
        .catch((err) => {
          console.log(err)
        })
    },
  },
}
</script>
