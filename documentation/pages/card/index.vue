<template lang="pug">
	main
		h1 Cards
		article
			Card.card
				slot(slot="img") 
					.img-container
						p Product img
				slot(slot="producto") Product name
				slot(slot="precio") Price
</template>
<style lang="scss" scoped>
main{
	margin: 5px 10px;
}

.img-container{
	width: 90px;
	height: 105px;
	display: flex;
	align-items: center;
	text-align: center;
}
</style>