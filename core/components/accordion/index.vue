<template lang="pug">
	.accordion
		.header
			.title
				.icon
					slot(name="icon")
				slot(name="servicio")
			.arrow
				IconArrowDown.icon(@click.native="openService" v-show="serviceClosed")
				IconArrowUp.icon(@click.native="closeService" v-show="serviceOpened")
		transition(name='fade-down')
			.content(v-show="serviceOpened")
				slot(name="img")
				slot(name="impresiones")
</template>
<script>

export default {
	data() {
		return {
			serviceOpened: false, 
			serviceClosed: true
		}
	},
	methods: {
		openService(){
			this.serviceOpened = !this.serviceOpened;
			this.serviceClosed = !this.serviceClosed
		},
		closeService(){
			this.serviceClosed = !this.serviceClosed;
			this.serviceOpened = !this.serviceOpened
		},
	}
}
</script>

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Manrope:wght@600&display=swap');

.accordion{
	display: flex;
	flex-direction: column;
	padding: 0 8px;
}

.header{
	display: flex;
	justify-content: space-between;
	border-bottom: .5px solid var(--static-grey-200);
	padding: 2.5px 0;
}

.title{
	display: flex;
	gap: 5px;
	align-items: center;
	font-family: 'Manrope', sans-serif;
	font-size: 20px;
}

.icon{
	justify-self: flex-end;
	color: var(--fill-accent-400);
}

.icon{
	width: 25px;
	display: flex;
	align-self: center;
}

.content{
	padding: 15px 10px;
	display: grid;
	grid-template-columns: repeat(3, 1fr);
	grid-auto-rows: 35px;
	gap: 10px 5px;
}

.fade-down {
	&-enter{
	opacity: 0;

		&-active{
			transition: all 0.8s ease, opacity 0.2s;
		}

		&-to{
			opacity: 1;
		}
	}

	&-leave{
		opacity: 1;

		&-active{
			transition: all 0.1s ease, opacity 0.2s;
		}

		&-to{
			opacity: 0;
		}
	}
}
</style>