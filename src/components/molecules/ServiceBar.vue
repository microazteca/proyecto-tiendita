<template lang="pug">
.bar
  .bar__container
    slot(name="src")
    p.bar__text
      slot(name="servicio")
  DownArrowServices.bar__arrow
  UpArrowServices.bar__arrow.bar__arrow--up
</template>

<script>
import DownArrowServices from "@/components/atoms/DownArrowServices.vue";
import UpArrowServices from "@/components/atoms/UpArrowServices.vue";
export default {
  props: {
    src: { type: String },
  },
  components: {
    UpArrowServices,
    DownArrowServices,
  },
};
</script>


<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css2?family=Manrope:wght@600&display=swap");
.bar {
  display: flex;
  justify-content: space-between;
  &__container {
    display: flex;
    align-self: flex-end;
    gap: 5px;
  }

  &__svg {
    color: var(--icon-services-color);
  }

  &__text {
    font-size: 20px;
    font-family: "Manrope", sans-serif;
  }

  &__arrow {
    color: var(--icon-services-color);

    &--up{
      display: none;
    }
  }
}
</style>
