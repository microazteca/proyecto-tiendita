<template lang="pug">
.services
  h1.services__h1 Servicios
  ServiceBar
    slot(slot="servicio") Pagos
  ServiceBar
    slot(slot="servicio") Recargas
  ServiceBar
    slot(slot="servicio") Copias e impresiones
  ServiceBar
    slot(slot="servicio") Retiros
</template>
<script>
import ServiceBar from "@/components/molecules/ServiceBar.vue";
import IconMobile from "@/components/atoms/IconMobile.vue";

export default {
  components: {
    ServiceBar,
    IconMobile,
  },
};
</script>

<style lang="scss" scoped>
.services {
  margin: 10px 0;
  padding: 0 16px;
  &__h1 {
    font-size: 24px;
  }
}
</style>