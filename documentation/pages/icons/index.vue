<template lang="pug">
main
	h1 Icons
	p When we create a component for an icon, we use the prefix icon before the name we want to assign. Example: iconWhatsApp, iconPrinter, iconArrowUp.
	h2 Props:
	ul
		li Width: 40px
		li Height: 40px
		li Fill-color: currentColor (this way we can assign a color through the css parent component)
	article
		h2 Icons collection
		.content
			.icon-container
				p IconArrowDouble
				IconArrowDouble.icon
			.icon-container
				p IconArrowDown
				IconArrowDown.icon
			.icon-container
				p IconArrowUp
				IconArrowUp.icon
			.icon-container
				p IconCard
				IconCard.icon
			.icon-container
				p IconCash
				IconCash.icon
			.icon-container
				p IconLocation
				IconLocation.icon
			.icon-container
				p IconMobile
				IconMobile.icon
			.icon-container
				p IconPrinter
				IconPrinter.icon
			.icon-container
				p IconSeeMore
				IconSeeMore.icon
			.icon-container
				p IconWhatsapp
				IconWhatsapp.icon
			.icon-container
				p IconSearch
				IconSearch.icon
</template>
<style lang="scss" scoped>
main{
	margin: 0 5px 15px;
}

.content{
	display: flex;
}

.icon-container{
	display: flex;
	border: 2px solid;
	flex-direction: column;
	justify-content: center;
	align-items: center;
	padding: 5px;
	margin: 0 2.5px;
	gap: 5px;
}

p{
	margin: 0;
}

.icon{
	width: 40px;
	height: 40px;
}
</style>