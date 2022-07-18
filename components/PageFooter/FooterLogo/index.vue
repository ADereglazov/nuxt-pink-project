<template>
  <nuxt-link
    :data-not-index-page="$route.path !== '/'"
    to="/"
    class="footer-logo"
    aria-label="Логотип Pink"
  >
    <svg class="footer-logo-image" width="146" height="40" role="img">
      <use xlink:href="~/assets/img/sprite.svg#logo-pink-mobile"></use>
    </svg>
    <svg
      class="footer-logo-image footer-logo-image--desktop"
      width="146"
      height="40"
      role="img"
    >
      <use xlink:href="~/assets/img/sprite.svg#logo-pink-desktop"></use>
    </svg>
  </nuxt-link>
</template>

<script>
export default {
  name: "FooterLogo",
};
</script>

<style lang="less" scoped>
.footer-logo {
  cursor: default;

  &[data-not-index-page] {
    &:hover {
      cursor: pointer;
    }

    &:hover &-image {
      color: @pink;
    }

    &:active &-image {
      fill: @pink-opacity03;
      color: @blue-dark-opacity03;
    }
  }

  &-image {
    display: block;
    fill: @pink;
    color: @blue-dark;

    &--desktop {
      display: none;
    }
  }

  @media (min-width: @tablet-width) {
    margin-top: -19px;
  }

  @media (min-width: @desktop-width) {
    padding-right: 10px;
    margin-top: -19px;

    &-image {
      display: none;

      &--desktop {
        display: block;
      }
    }
  }
}
</style>
