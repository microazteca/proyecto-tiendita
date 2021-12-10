<template lang="pug">
.bar
  .bar__header
    .bar__title
      .bar__icon
        slot(name="src")
      p.bar__text
        slot(name="servicio")
    DownArrowServices.bar__arrow(@click.native="openService()" v-show="serviceClosed")
    UpArrowServices.bar__arrow.bar__arrow--up(@click.native="closeService()" v-show="serviceOpened")
  .bar__content(v-show="serviceOpened")
    slot.bar__content-img(name="img")
</template>

<script>
import DownArrowServices from "@/components/atoms/DownArrowServices.vue";
import UpArrowServices from "@/components/atoms/UpArrowServices.vue";

export default {
  props: {
    src: { type: String },
    img: { type: String },
  },
  components: {
    UpArrowServices,
    DownArrowServices,
  },
  data() {
    return { serviceOpened: false, serviceClosed: true };
  },
  methods: {
    openService() {
      this.serviceOpened = !this.serviceOpened;
      this.serviceClosed = !this.serviceClosed;
    },
    closeService() {
      this.serviceClosed = !this.serviceClosed;
      this.serviceOpened = !this.serviceOpened;
    },
  },
};
</script>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css2?family=Manrope:wght@600&display=swap");
.bar {
  display: flex;
  flex-direction: column;
  padding: 8px;
  border-bottom: solid 1px var(--boder-services-color);

  &__header {
    display: flex;
    width: 100%;
    justify-content: space-between;
  }

  &__title {
    display: flex;
    align-self: flex-end;
    align-items: center;
    gap: 5px;
  }

  &__icon {
    display: flex;
    color: var(--icon-services-color);
    width: 26px;
  }

  &__text {
    font-size: 20px;
    font-family: "Manrope", sans-serif;
  }

  &__arrow {
    color: var(--icon-services-color);
    width: 26px;
  }

  &__content {
    display: grid;
    justify-content: center;
    align-items: center;
    grid-template-columns: repeat(3, auto);
    grid-template-rows: repeat(auto, 50px);
    grid-gap: 5px;
  }
}
</style>
