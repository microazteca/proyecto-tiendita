<template lang="pug">
	footer.footer
		a(:href="'https://goo.gl/maps/GVneKYoNhcK8nk5P8'" target="_blank").content.content--location
			IconLocation.icon
		a(:href="'https://api.whatsapp.com/send/?phone=529984595774'" target="_blank").content.content--whatsapp
			IconWhatsapp.icon
</template>
<style lang="scss" scoped>
.footer{
	display: flex;
	position: fixed;
	bottom: 0;
	width: 100%;
	height: 35px;
}

.content{
	width: 50%;
	display: flex;
	justify-content: center;

	&--location{
		background: var(--static-primary);
	}

	&--whatsapp{
	background: var(--static-accent);
	}
}

.icon{
	width: 25px;
	color: var(--static-white);
}
</style>