<template lang="pug">
	.card
		.top
			slot(name="img")
		.bottom
			.product
				slot(name="producto")
			.price
				slot(name="precio")
</template>
<style lang="scss" scoped>
.card{
	background-color: var(--static-accent-100);
	display: flex;
	flex-direction: column;
	border-radius: 15px;
	padding: 20px 5px 10px;
	justify-content: space-around;
	gap: 5px;
	justify-self: center;
	width: 100%;
}

.top{
	display: flex;
	justify-content: center;
}

.bottom{
	display: flex;
	flex-direction: column;
	text-align: center;
	gap: 8px;
}

.product{
	font-size: 18px;
	color: var(--static-grey)
}

.price{
	font-size: 20px;
	color: var(--static-black);
}

.product, .price{
	font-family: 'Manrope', sans-serif;
}


</style>
