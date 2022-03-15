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
      serviceClosed: true,
    }
  },
  methods: {
    openService() {
      this.serviceOpened = !this.serviceOpened
      this.serviceClosed = !this.serviceClosed
    },
    closeService() {
      this.serviceClosed = !this.serviceClosed
      this.serviceOpened = !this.serviceOpened
    },
  },
}
</script>

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Manrope:wght@600&display=swap');

.accordion {
  display: flex;
  flex-direction: column;
  padding: 0 8px;
}

.header {
  display: flex;
  justify-content: space-between;
  border-bottom: 0.5px solid var(--static-grey-200);
  padding: 2.5px 0;
}

.title {
  display: flex;
  gap: 5px;
  align-items: center;
  font-family: 'Manrope', sans-serif;
  font-size: 22px;
}

.icon {
  width: 30px;
  display: flex;
  align-self: center;
  justify-self: flex-end;
  color: var(--fill-accent-400);
}

.content {
  // margin: 15px 10px;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-auto-rows: 50px;
  gap: 10px 5px;
  overflow: hidden;
}

.fade-down {
  &-enter {
    opacity: 0;
    max-height: 0;

    &-active {
      transition: max-height 2s;
    }

    &-to {
      opacity: 1;
      max-height: 1000px;
    }
  }

  &-leave {
    opacity: 1;
    max-height: 1000px;

    &-active {
      transition: max-height .5s;
    }

    &-to {
      max-height: 0;
    }
  }
}
</style>
