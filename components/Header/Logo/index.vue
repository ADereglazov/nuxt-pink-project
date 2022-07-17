<template>
  <a class="logo" aria-label="Логотип Pink">
    <svg class="logo-image" width="74" height="23" role="img">
      <use xlink:href="~/assets/img/sprite.svg#logo-mobile"></use>
    </svg>
    <svg class="logo-image logo-image--tablet" width="146" height="40" role="img">
      <use xlink:href="~/assets/img/sprite.svg#logo-tablet"></use>
    </svg>
    <svg class="logo-image logo-image--desktop" width="146" height="40" role="img">
      <use xlink:href="~/assets/img/sprite.svg#logo-desktop"></use>
    </svg>
  </a>
</template>

<script>
export default {
  name: 'Logo'
}
</script>

<style lang="less" scoped>
@import (reference) "./assets/styles/styles.less";

.logo {
  cursor: pointer;

  &:hover .logo-image {
    color: @pink;
    fill: @pink;
  }

  &:active .logo-image {
    color: @pink-opacity03;
    fill: @pink-opacity03;
  }

  @media (max-width: @mobile-width-only) {
    position: absolute;
    top: 22px;
    left: 20px;
  }

  @media (min-width: @tablet-width) {
    top: 30px;

    .main-nav__logo-image {
      display: none;

      &--tablet {
        display: block;
      }
    }
  }

  @media (min-width: @desktop-width) {
    top: auto;
    margin-top: 27px;
  }

  &-image {
    display: block;
    color: @pink;
    fill: @white;

    &--tablet,
    &--desktop {
      display: none;
    }

    @media (min-width: @tablet-width) {
      display: none;

      &--tablet {
        display: block;
      }
    }

    @media (min-width: @desktop-width) {
      &--tablet {
        display: none;
      }

      &--desktop {
        display: block;
      }
    }
  }
}
</style>
