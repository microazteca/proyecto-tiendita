<template lang="pug">
	a(:href="'#top'")
		IconArrowDouble.arrow
</template>
<style lang="scss" scoped>
.arrow{
	position: fixed;
	right: 2px;
	bottom: 80px;
	width: 30px;
	color: var(--static-primary-700);
	z-index: 200;
}
</style>