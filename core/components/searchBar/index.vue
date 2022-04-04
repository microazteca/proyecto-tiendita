<template lang="pug">
	.searchBar
		p ¿Qué estás buscando?
		IconSearch.icon
</template>
<style lang="scss" scoped>
.searchBar{
	display: flex;
	background-color: var(--static-primary-100);
	border-radius: 19px;
	justify-content: space-between;
	border: solid 1px var(--static-grey-600);
	padding: 5px 10px;
	margin: 0 10px;
}

p{
	font-size: 18px;
	font-weight: 400;
	font-family: 'Manrope', sans-serif;
	color: var(--static-grey-600);
}

.icon{
	width: 18px;
	color: var(--static-grey-600);
}
</style>
