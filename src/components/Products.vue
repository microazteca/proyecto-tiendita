<template lang="pug">
	.products
		h2.title Productos
		SearchBar.search-bar
		.grid
			Card
				slot(slot="img")
					.img-container
						img(src="@/assets/img/productos/takis.png")
				slot(slot="producto") Takis Fuego
				slot(slot="precio") $15.00
			Card
				slot(slot="img")
					.img-container
						img(src="@/assets/img/productos/runners.png")
				slot(slot="producto") Runners Fuego
				slot(slot="precio") $10.00
			Card
				slot(slot="img")
					.img-container
						img(src="@/assets/img/productos/sabritas-habanero.jpeg")
				slot(slot="producto") Sabritas Habanero
				slot(slot="precio") $15.00
			Card
				slot(slot="img")
					.img-container
						img(src="@/assets/img/productos/takis.png")
				slot(slot="producto") Takis Fuego
				slot(slot="precio") $15.00
			Card
				slot(slot="img")
					.img-container
						img(src="@/assets/img/productos/takis.png")
				slot(slot="producto") Takis Fuego
				slot(slot="precio") $15.00
</template>
<style lang="scss" scoped>
.products{
	display: flex;
	flex-direction: column;
	margin: 10px 10px 50px;
}

.title{
	color: var(--text-black);
	font-size: 26px;
	margin-bottom: 5px;
}


.grid{
	margin-top: 13px;
	width: 100%;
	display: grid;
	grid-template-columns: repeat(2, 1fr);
	gap: 18px;
	padding: 0 10px;
}

.img-container{
	width: 100%;
	display: flex;
	justify-content: center;
}

img{
	width: 100px;
	object-fit: cover;
}
</style>