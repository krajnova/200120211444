<template>
  <div class="consultant-services">
    <h2 class="consultant-services__header">Услуг</h2>
    <hr
      class="consultant-services__line consultant-services__line--top"
      noshade
    />
    <div class="consultant-services__list">
      <div
        v-for="service in services"
        class="consultant-services__item service"
        :key="'service' + service.id"
      >
        <div class="service__scale-container">
          <div
            class="service__scale"
            :style="{
              width: Math.floor((service.amount / servicesSum) * 100) + '%'
            }"
          ></div>
          <div class="service__name">{{ service.name }}</div>
          <div class="service__rate">{{ service.amount }}</div>
        </div>
      </div>
    </div>
    <hr
      class="consultant-services__line consultant-services__line--bottom"
      noshade
    />
    <div class="consultant-services__total">
      <div class="service__total-header">Всего</div>
      <div class="service__total-amount">{{ servicesSum }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ConsultantServices",

  data: () => {
    return {
      servicesSum: 0
    };
  },

  props: {
    services: Array
  },

  created() {
    this.services.forEach(service => (this.servicesSum += service.amount));
  }
};
</script>

<style lang="scss" scoped>
.consultant-services {
  &__header {
    display: flex;
    justify-content: flex-end;
    padding-right: 40px;
    font-size: 13px;
    line-height: 15px;
    font-weight: 400;
  }

  &__line {
    border: 1px solid #dadada;
    background-color: transparent;

    &--top {
      margin-top: 7px;
      margin-bottom: 16px;
    }

    &--bottom {
      margin-top: 15px;
      margin-bottom: 9px;
    }
  }

  &__list {
    border-left: 1px solid #dadada;
  }

  &__total {
    display: flex;
    justify-content: space-between;
    padding-right: 40px;
    font-weight: 700;
  }

  &__total-header {
    font-size: 16px;
    line-height: 26px;
  }

  &__total-sum {
    font-size: 16px;
    line-height: 15px;
  }
}

.service {
  position: relative;
  display: flex;
  justify-content: flex-end;

  &:hover .service__scale {
    background-color: #b1e19b;
  }

  &__scale-container {
    display: flex;
    justify-content: space-between;
    padding-right: 40px;
    padding-left: 6px;
    width: 100%;
  }

  &__scale {
    position: absolute;
    left: 0;
    height: 100%;
    z-index: -1;
    background-color: #ace2f8;
    border: 1px solid #fff;
    border-left: none;
    border-radius: 0px 3px 3px 0px;
  }

  &__name {
    font-size: 13px;
    line-height: 26px;
  }

  &__rate {
    display: flex;
    justify-content: flex-end;
    align-items: center;
    max-width: 40px;
    width: 100%;
    font-weight: 700;
    font-size: 13px;
    line-height: 15px;
  }
}
</style>
