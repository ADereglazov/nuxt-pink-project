<template>
  <section class="download">
    <h2 class="visually-hidden">Скачать приложение Pink</h2>
    <div class="download__container container">
      <div class="download__wrapper">
        <p class="download__title">Взгляните на жизнь иначе!</p>
        <picture>
          <source
            type="image/webp"
            media="(min-width: 960px)"
            srcset="
              ~/assets/img/iphone-hand-desktop@1x.webp 1x,
              ~/assets/img/iphone-hand-desktop@2x.webp 2x
            "
          />
          <source
            type="image/webp"
            media="(min-width: 660px)"
            srcset="
              ~/assets/img/iphone-hand-tablet@1x.webp 1x,
              ~/assets/img/iphone-hand-tablet@2x.webp 2x
            "
          />
          <source
            type="image/webp"
            srcset="
              ~/assets/img/iphone-hand-mobile@1x.webp 1x,
              ~/assets/img/iphone-hand-mobile@2x.webp 2x
            "
          />
          <source
            media="(min-width: 960px)"
            srcset="
              ~/assets/img/iphone-hand-desktop@1x.png 1x,
              ~/assets/img/iphone-hand-desktop@2x.png 2x
            "
          />
          <source
            media="(min-width: 660px)"
            srcset="
              ~/assets/img/iphone-hand-tablet@1x.png 1x,
              ~/assets/img/iphone-hand-tablet@2x.png 2x
            "
          />
          <img
            class="download__image-main"
            src="~/assets/img/iphone-hand-mobile@1x.png"
            srcset="~/assets/img/iphone-hand-mobile@2x.png 2x"
            width="258"
            height="286"
            alt="Телефон в руке"
          />
        </picture>
        <a
          class="download__button"
          href="https://www.apple.com/ru/ios/app-store"
          target="_blank"
          rel="noopener"
          aria-label="Apple Store"
          >Скачать приложение</a
        >
        <ul class="download__list">
          <li
            v-for="item in downloadList"
            :key="item.name"
            class="download__item"
          >
            <a
              :href="item.link"
              :aria-label="item.name"
              class="download__link"
              target="_blank"
              rel="noopener"
            >
              <svg
                :width="item.image.width"
                :height="item.image.height"
                class="download__image"
                role="img"
              >
                <use :xlink:href="iconSrc(item.image.iconId)"></use>
              </svg>
            </a>
          </li>
        </ul>
        <p class="download__text">
          Доступно для iPhone, iPad, Android, Windows Phone, OS X, Windows 8
        </p>
      </div>
    </div>
  </section>
</template>

<script>
const SPRITE = require("~/assets/img/sprite.svg");

export default {
  name: "DownloadSection",
  data: () => ({
    downloadList: [
      {
        name: "Apple Store",
        link: "https://www.apple.com/ru/ios/app-store",
        image: {
          width: 47,
          height: 56,
          iconId: "#logo-apple",
        },
      },
      {
        name: "Play Market",
        link: "https://play.google.com/store",
        image: {
          width: 43,
          height: 47,
          iconId: "#logo-android",
        },
      },
      {
        name: "Windows Store",
        link: "https://www.microsoft.com/ru-ru/store/",
        image: {
          width: 44,
          height: 41,
          iconId: "#logo-microsoft",
        },
      },
    ],
  }),
  methods: {
    iconSrc(id) {
      return SPRITE + id;
    },
  },
};
</script>

<style lang="less" scoped>
.download {
  color: @white;
  background-repeat: no-repeat;
  background-position: top center;
  background-size: contain;
  background-color: @blue-darken;
  background-image: linear-gradient(
      to bottom,
      transparent 63%,
      @blue-darken 63%
    ),
    url("~assets/img/bg-back-mobile@1x.jpg");

  @media (min-resolution: @retina-dpi), (min-resolution: @retina-dppx) {
    background-image: linear-gradient(
        to bottom,
        transparent 63%,
        @blue-darken 63%
      ),
      url("~assets/img/bg-back-mobile@2x.jpg");
  }

  &__wrapper {
    display: flex;
    flex-direction: column;
    min-height: 735px;
    text-align: center;
    padding-top: 90px;
    padding-bottom: 20px;
  }

  &__image-main {
    display: block;
    width: 258px;
    height: 286px;
    margin-left: -20px;
  }

  &__title {
    font-size: 24px;
    font-weight: 300;
    line-height: 30px;
    margin-top: 0;
    margin-bottom: 26px;
  }

  &__button {
    display: block;
    width: 280px;
    min-height: 55px;
    font-size: 18px;
    font-weight: 700;
    line-height: 18px;
    text-decoration: none;
    text-align: center;
    padding: 13px 10px 10px 10px;
    border: 3px solid @white;
    border-radius: 27px;
    margin: 29px auto 30px;
    color: @white;
    background-color: transparent;

    &:hover {
      color: @pink;
      background-color: @white;
      border-color: @white;
    }

    &:active {
      outline: none;
      color: @pink-opacity03;
      background-color: @white;
      border-color: @white;
    }
  }

  &__list {
    .list-reset();
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    align-items: flex-end;
    width: 205px;
    margin-right: auto;
    margin-left: auto;
  }

  &__item:nth-child(3) {
    margin-bottom: 3px;
  }

  &__image {
    display: block;
  }

  &__text {
    font-weight: 300;
    margin-top: 24px;
    margin-bottom: 0;
  }

  @media (min-width: 525px) {
    background-position: center;
    background-size: cover;
  }
}

@media (min-width: @tablet-width) {
  .download {
    background-position: center;
    background-size: cover;
    background-image: url("~assets/img/bg-back-tablet@1x.jpg");

    @media (min-resolution: @retina-dpi), (min-resolution: @retina-dppx) {
      background-image: url("~assets/img/bg-back-tablet@2x.jpg");
    }
  }

  .download__container {
    position: relative;
    z-index: 0;
  }

  .download__wrapper {
    width: 300px;
    min-height: 729px;
    padding-top: 202px;
  }

  .download__title {
    font-size: 40px;
    line-height: 49px;
    padding-right: 28px;
    padding-left: 30px;
    margin-bottom: 30px;
  }

  .download__button {
    width: 300px;
    margin-top: 0;
    margin-bottom: 45px;
  }

  .download__image-main {
    position: absolute;
    right: 0;
    bottom: 0;
    margin: 0;
    width: 700px;
    height: 545px;
    object-fit: cover;
    z-index: -1;
  }

  .download__text {
    font-size: 18px;
    margin-top: 36px;
  }
}

@media (min-width: @desktop-width) {
  .download {
    overflow: hidden;
    background-image: url("~assets/img/bg-back-desktop@1x.jpg");

    @media (min-resolution: @retina-dpi), (min-resolution: @retina-dppx) {
      background-image: url("~assets/img/bg-back-desktop@2x.jpg");
    }
  }

  .download__wrapper {
    min-height: 853px;
    padding-top: 220px;
  }

  .download__title {
    font-size: 50px;
    line-height: 60px;
    margin-bottom: 52px;
  }

  .download__image-main {
    left: 70px;
    width: 1050px;
    height: 645px;
  }

  .download__button {
    font-size: 21px;
    margin-bottom: 65px;
  }

  .download__text {
    margin-top: 55px;
  }
}
</style>
