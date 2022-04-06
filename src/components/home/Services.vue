<template lang="pug">
  .services
    h2.title Servicios
    .grid
      Accordion.accordion
        slot(slot="icon")
          IconCash
        slot(slot="servicio") Pagos
        slot(slot="img")
          .container
            img(src="@/assets/img/pagos/aguakan.png")
        slot(slot="img")
          .container
            img(src="@/assets/img/pagos/cfe.png")
        slot(slot="img")
          .container
            img(src="@/assets/img/pagos/dish.png")
        slot(slot="img")
          .container
            img(src="@/assets/img/pagos/izzi.png")
        slot(slot="img")
          .container
            img(src="@/assets/img/pagos/netflix.png")
        slot(slot="img")
          .container
            img(src="@/assets/img/pagos/infonavit.png")
        slot(slot="img")
          .container
            img(src="@/assets/img/pagos/total-play.svg")
      Accordion.accordion
        slot(slot="icon")
          IconMobile
        slot(slot="servicio") Recargas
        slot(slot="img")
          .container
            img(src="@/assets/img/recargas/att.png")
        slot(slot="img")
          .container
            img(src="@/assets/img/recargas/movistar.png")
        slot(slot="img")
          .container
            img(src="@/assets/img/recargas/telcel.png")
        slot(slot="img")
          .container
            img(src="@/assets/img/recargas/unefon.png")
      Accordion.accordion
        slot(slot="icon")
          IconPrinter
        slot(slot="servicio") Copias e impresiones
        slot(slot="impresiones")
          .container-text
            li Acta de nacimiento
            li CURP
            li RFC
            li Citas INE
            li Citas IMSS
            li Citas pasaporte
      Accordion.accordion
        slot(slot="icon")
          IconCard
        slot(slot="servicio") Retiros de efectivo
        slot(slot="img")
          .container
            img(src="@/assets/img/retiros/master-card.svg")
        slot(slot="img")
          .container
            img(src="@/assets/img/retiros/visa.png")
</template>
<style lang="scss" scoped>
.services {
  font-family: 'Poppins', sans-serif;
  display: flex;
  flex-direction: column;
  margin: 10px;
}

.title {
  color: var(--text-black);
  font-size: 26px;
  margin-bottom: 5px;

  @media (min-width: 1024px) {
    text-align: center;
    margin-bottom: 10px;
  }
}

.grid {
  @media (min-width: 1024px) {
    display: flex;
    flex-direction: column;
    gap: 10px 0;
    align-items: center;
  }
}

.accordion {
  @media (min-width: 1024px) {
    width: 80%;
  }
}

.container {
  width: 65px;
  height: 57px;
  padding: 0;

  @media (min-width: 768px) {
    width: 70px;
    height: 62px;
  }

  @media (min-width: 1024px) {
    width: 90px;
    height: 82px;
    padding: 5px;
  }
}

.container-text{
  padding: 0 10px;
  margin-bottom: 10px;

  @media (min-width: 768px) {
    padding: 0 25px;
    margin-bottom: 10px;
  }
}

img {
  width: 100%;
  height: 100%;
  object-fit: contain;
  margin: 5px 0;

  @media (min-width: 1024px) {
    background-color: var(--static-white);
    border-radius: 5px;
  }
}

ul {
  line-height: 1.5;
}

li {
  font-family: 'Manrope', sans-serif;
  font-size: 16px;
}
</style>
