<template lang="pug">
main
	h1 Accordions
	article
		Accordion
			slot(slot="icon")
				IconCash
			slot(slot="servicio") Pagos
			slot(slot="img")
				p This is the content you want to add to the accordion.
</template>
<style lang="scss" scoped>
</style>