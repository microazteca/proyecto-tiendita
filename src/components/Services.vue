<template lang="pug">
.services
  h1.services__h1 Servicios
  ServiceBar
    slot(slot="src") 
      IconCash
    slot(slot="servicio") Pagos
    slot(slot="img")
      img(src="@/assets/img/telcel.png")
      img(src="@/assets/img/telcel.png")
  ServiceBar
    slot(slot="src") 
        IconMobile
    slot(slot="servicio") Recargas
    slot(v-slot:default="props")
  ServiceBar
    slot(slot="src") 
        IconPrinter
    slot(slot="servicio") Copias e impresiones
  ServiceBar
    slot(slot="src") 
        IconCard
    slot(slot="servicio") Retiros
</template>
<script>
import ServiceBar from "@/components/molecules/ServiceBar.vue";
import IconCash from "@/components/atoms/IconCash.vue";
import IconMobile from "@/components/atoms/IconMobile.vue";
import IconPrinter from "@/components/atoms/IconPrinter.vue";
import IconCard from "@/components/atoms/IconCard.vue";
export default {
  components: {
    ServiceBar,
    IconCash,
    IconMobile,
    IconPrinter,
    IconCard,
  },
  props: ["props"],
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
