<template>
  <section class="effect">
    <div class="effect__wrapper container">
      <div class="effect__timer">
        <span class="effect__twenty-four">24</span>
        <svg
          class="effect__timer-image"
          width="238"
          height="276"
          role="img"
          aria-label="Таймер"
          focusable="false"
        >
          <use xlink:href="~/assets/img/sprite.svg#icon-timer"></use>
        </svg>
      </div>
      <div class="effect__text-wrapper">
        <h2 class="effect__header">
          Эффект<span class="effect__header-tablet-space">&nbsp;&nbsp;</span> на
          24 часа!
        </h2>
        <p class="effect__text">
          Британские ученые провели исследования и доказали,
          <span class="effect__header-desktop-space">&nbsp;&nbsp;&nbsp;</span>
          что положительный эффект
          <span class="effect__header-tablet-space">&nbsp;&nbsp;&nbsp;</span> от
          использования приложения длится целые сутки!
        </p>
        <a class="effect__link" href="#">Узнать больше об исследовании</a>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "EffectSection",
};
</script>

<style lang="less" scoped>
.effect {
  display: none;
}

@media (min-width: @tablet-width) {
  .effect {
    display: inherit;
    background-color: @white;
  }

  .effect__wrapper {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-top: 57px;
    padding-bottom: 20px;
  }

  .effect__timer {
    position: relative;
  }

  .effect__timer-image {
    width: 238px;
    height: 276px;
    fill: @gray-lighter;
  }

  .effect__twenty-four {
    position: absolute;
    display: block;
    width: 202px;
    height: 202px;
    font-size: 96px;
    font-weight: 700;
    text-align: center;
    line-height: 96px;
    padding-top: 32px;
    border: 15px solid @pink;
    border-radius: 50%;
    color: @pink;
    background-color: @white;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -85px);

    &:hover {
      cursor: default;
    }
  }

  .effect__text-wrapper {
    width: 310px;
    padding-top: 5px;
    padding-right: 10px;
  }

  .effect__header {
    font-size: 30px;
    font-weight: 700;
    line-height: 36px;
    width: 170px;
    margin: 0;
    color: @black;
  }

  .effect__text {
    margin-top: 10px;
    margin-bottom: 10px;
  }

  .effect__header-desktop-space {
    display: none;
  }

  .effect__header-tablet-space {
    display: inline-block;
  }

  .effect__link {
    color: @pink;
  }
}

@media (min-width: @desktop-width) {
  .effect {
    min-height: 475px;
    background-color: @gray-light;
  }

  .effect__wrapper {
    padding-top: 65px;
  }

  .effect__timer-image {
    width: 298px;
    height: 345px;
  }

  .effect__twenty-four {
    position: absolute;
    font-size: 120px;
    line-height: 120px;
    width: 253px;
    height: 253px;
    padding-top: 42px;
    border: 17px solid @pink;
    border-radius: 50%;
    color: @pink;
    background-color: @gray-light;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -105px);
  }

  .effect__text-wrapper {
    width: 540px;
    padding-top: 42px;
    padding-right: 0;
    margin-right: 33px;
  }

  .effect__header {
    font-size: 30px;
    line-height: 30px;
    width: 315px;
  }

  .effect__text,
  .effect__link {
    font-size: 18px;
    line-height: 30px;
  }

  .effect__text {
    margin-top: 25px;
    margin-bottom: 30px;
  }

  .effect__header-desktop-space {
    display: inline-block;
  }

  .effect__header-tablet-space {
    display: none;
  }
}
</style>
