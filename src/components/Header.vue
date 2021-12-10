<template lang="pug">
.header
  h1.header__h1 Atzin.com
</template>

<style lang="scss" scoped>
.header {
  height: 40px;
  background-color: var(--background-header-color);
		padding: 8px 24px;
		display: flex;
		justify-content: center;
		align-items: center;

  &__h1 {
				font-size: 32px;
				color: var(--text-header-color);
  }
}
</style>