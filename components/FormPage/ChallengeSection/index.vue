<template>
  <section class="challenge">
    <div class="challenge__wrapper container">
      <h2 class="challenge__text">
        Конкурс на самое безбашенное путешествие с Пинк
      </h2>
    </div>
  </section>
</template>

<script>
export default {
  name: "ChallengeSection",
};
</script>

<style lang="less" scoped>
.challenge {
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

.challenge__text {
  font-size: 24px;
  font-weight: 300;
  line-height: 30px;
  text-align: center;
  padding-top: 98px;
  padding-bottom: 233px;
  margin: 0 auto;
  color: @white;
}

@media (min-width: @tablet-width) {
  .challenge {
    min-height: 729px;
    margin-bottom: -288px;
    background: url("~assets/img/bg-back-tablet@1x.jpg") no-repeat @blue-darken;

    @media (min-resolution: @retina-dpi), (min-resolution: @retina-dppx) {
      background-image: url("~assets/img/bg-back-tablet@2x.jpg");
    }
  }

  .challenge__text {
    font-size: 50px;
    line-height: 60px;
    width: 480px;
    padding-top: 180px;
    padding-bottom: 300px;
  }
}

@media (min-width: @desktop-width) {
  .challenge {
    min-height: 853px;
    margin-bottom: -458px;
    background: url("~assets/img/bg-back-desktop@1x.jpg") no-repeat @blue-darken;

    @media (min-resolution: @retina-dpi), (min-resolution: @retina-dppx) {
      background-image: url("~assets/img/bg-back-desktop@2x.jpg");
    }
  }

  .challenge__text {
    width: 750px;
    padding-top: 173px;
    padding-bottom: 470px;
  }
}
</style>
