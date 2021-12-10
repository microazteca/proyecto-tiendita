<template lang="pug">
.services
  h1.services__h1 Servicios
  ServiceBar
    slot(slot="src") 
      IconCash
    slot(slot="servicio") Pagos
    slot(slot="img")
      img(src="@/assets/img/recargas/telcel.png")
      img(src="@/assets/img/recargas/movistar.png")
      img(src="@/assets/img/recargas/att.png")
      img(src="@/assets/img/recargas/unefon.png")
  ServiceBar
    slot(slot="src") 
        IconMobile
    slot(slot="servicio") Recargas
    slot(v-slot:default="props")
    slot(slot="img")
      img(src="@/assets/img/pagos/dish.png")
      img(src="@/assets/img/pagos/sky.png")
      img(src="@/assets/img/pagos/netflix.png")
      img(src="@/assets/img/pagos/telmex.png")
      img(src="@/assets/img/pagos/aguakan.png")
      img(src="@/assets/img/pagos/cfe.png")
      img(src="@/assets/img/pagos/spotify.png")
      img(src="@/assets/img/pagos/izzi.png")
  ServiceBar
    slot(slot="src") 
        IconPrinter
    slot(slot="servicio") Copias e impresiones
    slot(slot="img")
      img(src="@/assets/img/recargas/telcel.png")
      img(src="@/assets/img/recargas/movistar.png")
      img(src="@/assets/img/recargas/att.png")
      img(src="@/assets/img/recargas/unefon.png")
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
