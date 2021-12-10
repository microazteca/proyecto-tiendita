<template lang="pug">
footer.footer
  a(href="#").footer__section
    img.footer__svg(src="@/assets/svg/icon-location.svg")
  a(href="#").footer__section.footer__section--whats
    img.footer__svg(src="@/assets/svg/icon-whats.svg")
</template>
<style lang="scss" scoped>
.footer {
  display: flex;
		width: 100%;
		height: 35px;
		position: fixed;
    bottom: 0;
  &__section {
    display: flex;
    width: 50%;
    justify-content: center;
    background-color: var(--background-footer-primary-color);

    &--whats {
      background-color: var(--background-footer-secondary-color);
    }
  }

  &__svg {
    width: 25px;
  }
}
</style>