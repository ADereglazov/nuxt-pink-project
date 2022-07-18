<template>
  <div class="copyright">
    <span class="copyright__text">Разработано</span>
    <a
      class="copyright__link"
      href="https://htmlacademy.ru/intensive/adaptive"
      aria-label="HTML Academy"
    >
      <svg class="copyright__image" width="27" height="34" role="img">
        <use xlink:href="~/assets/img/sprite.svg#logo-htmlacademy"></use>
      </svg>
    </a>
  </div>
</template>

<script>
export default {
  name: "CopyRight",
};
</script>

<style lang="less" scoped>
.copyright {
  max-width: 280px;

  &__text {
    font-weight: 400;
    line-height: 18px;
  }

  &__link {
    margin-left: 12px;
  }

  &__image {
    color: @pink;
    vertical-align: middle;

    &:hover {
      color: @blue-dark;
    }

    &:active {
      color: @blue-dark-opacity01;
    }
  }

  @media (min-width: @tablet-width) {
    padding-left: 15px;
  }

  @media (min-width: @desktop-width) {
    padding-left: 0;

    &__text {
      font-size: 18px;
    }

    &__link {
      margin-left: 10px;
    }
  }
}
</style>
