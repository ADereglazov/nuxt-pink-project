<template>
  <section class="photos">
    <div class="photos__wrapper container">
      <h2 class="photos__text">Фотографии пользователей</h2>
    </div>
  </section>
</template>

<script>
export default {
  name: "PhotosSection",
};
</script>

<style lang="less" scoped>
.photos {
  min-height: 462px;
  margin-bottom: -223px;
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  background-color: @blue-darken;
  background-image: url("~assets/img/bg-back-mobile@1x.jpg");

  @media (min-resolution: @retina-dpi), (min-resolution: @retina-dppx) {
    background-image: url("~assets/img/bg-back-mobile@2x.jpg");
  }
}

.photos__text {
  font-size: 24px;
  font-weight: 300;
  line-height: 30px;
  text-align: center;
  width: 170px;
  padding-top: 98px;
  padding-bottom: 233px;
  margin: 0 auto;
  color: @white;
}

@media (min-width: @tablet-width) {
  .photos {
    min-height: 729px;
    margin-bottom: -288px;
    background-image: url("~assets/img/bg-back-tablet@1x.jpg");

    @media (min-resolution: @retina-dpi), (min-resolution: @retina-dppx) {
      background-image: url("~assets/img/bg-back-tablet@2x.jpg");
    }
  }

  .photos__text {
    font-size: 50px;
    line-height: 60px;
    width: 360px;
    padding-top: 182px;
    padding-bottom: 300px;
  }
}

@media (min-width: @desktop-width) {
  .photos {
    min-height: 853px;
    margin-bottom: -458px;
    background-image: url("~assets/img/bg-back-desktop@1x.jpg");

    @media (min-resolution: @retina-dpi), (min-resolution: @retina-dppx) {
      background-image: url("~assets/img/bg-back-desktop@2x.jpg");
    }
  }

  .photos__text {
    padding-top: 173px;
    padding-bottom: 470px;
  }
}
</style>
