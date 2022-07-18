<template>
  <div class="social">
    <ul class="social__list">
      <li class="social__item">
        <a class="social__link" href="#" aria-label="Твиттер">
          <svg class="social__image" width="18" height="14" role="img">
            <use xlink:href="~/assets/img/sprite.svg#icon-twitter"></use>
          </svg>
        </a>
      </li>
      <li class="social__item">
        <a class="social__link" href="#" aria-label="Фейсбук">
          <svg class="social__image" width="9" height="18" role="img">
            <use xlink:href="~/assets/img/sprite.svg#icon-facebook"></use>
          </svg>
        </a>
      </li>
      <li class="social__item">
        <a class="social__link" href="#" aria-label="YouTube">
          <svg class="social__image" width="15" height="13" role="img">
            <use xlink:href="~/assets/img/sprite.svg#icon-youtube"></use>
          </svg>
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "SocialsIcons",
};
</script>

<style lang="less" scoped>
.social__list {
  .list-reset();
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  width: 174px;
}

.social__link {
  display: block;
  position: relative;
  width: 46px;
  height: 46px;
  border: 3px solid @blue-dark-opacity01;
  border-radius: 50%;

  &:hover {
    border-color: @blue-dark;
  }

  &:active {
    opacity: 0.1;
  }
}

.social__image {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: @pink;
}
</style>
