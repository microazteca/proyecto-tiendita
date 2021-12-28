<template lang="pug">
	header.header#top
		a(:href="'/'" title="home")
			h1.title Atzin.com
</template>
<style lang="scss" scoped>
.header{
	width: 100%;
	background: var(--static-primary);
	text-align: center;
}

.title{
	color: var(--static-white);
}
</style>