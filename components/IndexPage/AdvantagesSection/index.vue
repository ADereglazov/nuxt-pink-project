<template>
  <section class="advantages">
    <header class="advantages__header">
      <div class="advantages__container container">
        <h2 class="visually-hidden">Преимущества приложения Pink</h2>
        <p class="advantages__intro">Устали от серости мегаполиса?</p>
        <p class="advantages__intro">Нам есть, что вам предложить!</p>
      </div>
    </header>
    <div class="advantages__wpapper">
      <div class="advantages__content container">
        <ul class="advantages__list">
          <li
            v-for="item in advantagesList"
            :key="item.title + item.text"
            class="advantages__item"
          >
            <h3 class="advantages__title">{{ item.title }}</h3>
            <p class="advantages__text">{{ item.text }}</p>
          </li>
        </ul>
        <div class="advantages__images">
          <picture>
            <source
              type="image/webp"
              media="(min-width: 960px)"
              srcset="
                ~/assets/img/iphone-screen-1-desktop@1x.webp 1x,
                ~/assets/img/iphone-screen-1-desktop@2x.webp 2x
              "
            />
            <source
              type="image/webp"
              media="(min-width: 660px)"
              srcset="
                ~/assets/img/iphone-screen-1-tablet@1x.webp 1x,
                ~/assets/img/iphone-screen-1-tablet@2x.webp 2x
              "
            />
            <source
              media="(min-width: 960px)"
              srcset="
                ~/assets/img/iphone-screen-1-desktop@1x.png 1x,
                ~/assets/img/iphone-screen-1-desktop@2x.png 2x
              "
            />
            <source
              media="(min-width: 660px)"
              srcset="
                ~/assets/img/iphone-screen-1-tablet@1x.png 1x,
                ~/assets/img/iphone-screen-1-tablet@2x.png 2x
              "
            />
            <img
              class="advantages__image advantages__image--hide"
              src="#"
              alt="Iphone черно-белый"
            />
          </picture>
          <picture>
            <source
              type="image/webp"
              media="(min-width: 960px)"
              srcset="
                ~/assets/img/iphone-screen-2-desktop@1x.webp 1x,
                ~/assets/img/iphone-screen-2-desktop@2x.webp 2x
              "
            />
            <source
              type="image/webp"
              media="(min-width: 660px)"
              srcset="
                ~/assets/img/iphone-screen-2-tablet@1x.webp 1x,
                ~/assets/img/iphone-screen-2-tablet@2x.webp 2x
              "
            />
            <source
              media="(min-width: 960px)"
              srcset="
                ~/assets/img/iphone-screen-2-desktop@1x.png 1x,
                ~/assets/img/iphone-screen-2-desktop@2x.png 2x
              "
            />
            <source
              media="(min-width: 660px)"
              srcset="
                ~/assets/img/iphone-screen-2-tablet@1x.png 1x,
                ~/assets/img/iphone-screen-2-tablet@2x.png 2x
              "
            />
            <img
              class="advantages__image advantages__image--hide"
              src="#"
              alt="Iphone розовый"
            />
          </picture>
          <picture>
            <source
              type="image/webp"
              media="(min-width: 960px)"
              srcset="
                ~/assets/img/iphone-screen-3-desktop@1x.webp 1x,
                ~/assets/img/iphone-screen-3-desktop@2x.webp 2x
              "
            />
            <source
              type="image/webp"
              media="(min-width: 660px)"
              srcset="
                ~/assets/img/iphone-screen-3-tablet@1x.webp 1x,
                ~/assets/img/iphone-screen-3-tablet@2x.webp 2x
              "
            />
            <source
              type="image/webp"
              srcset="
                ~/assets/img/iphone-screen-mobile@1x.webp 1x,
                ~/assets/img/iphone-screen-mobile@2x.webp 2x
              "
            />
            <source
              media="(min-width: 960px)"
              srcset="
                ~/assets/img/iphone-screen-3-desktop@1x.png 1x,
                ~/assets/img/iphone-screen-3-desktop@2x.png 2x
              "
            />
            <source
              media="(min-width: 660px)"
              srcset="
                ~/assets/img/iphone-screen-3-tablet@1x.png 1x,
                ~/assets/img/iphone-screen-3-tablet@2x.png 2x
              "
            />
            <img
              class="advantages__image"
              src="~/assets/img/iphone-screen-mobile@1x.png"
              srcset="~/assets/img/iphone-screen-mobile@2x.png 2x"
              width="157"
              height="320"
              alt="Iphone смайл"
            />
          </picture>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "AdvantagesSection",
  data: () => ({
    advantagesList: [
      {
        title: "Поднимает настроение",
        text: "Приложение позволит вам победить осеннюю хандру и депрессию буквально в несколько кликов!",
      },
      {
        title: "Меняет мир вокруг",
        text: "Сделайте снимок и украсьте его смайликом или текстовой подписью, чтобы усилить эффект",
      },
      {
        title: "Заводит новых друзей",
        text: "Ставьте лайки, комментируйте, делитесь фотографиями с друзьями и заводите новых",
      },
    ],
  }),
};
</script>

<style lang="less" scoped>
.advantages__header {
  font-size: 24px;
  font-weight: 300;
  line-height: 30px;
  text-align: center;
  background-color: @white;
}

.advantages__wpapper {
  background-image: url("~assets/img/bg-triangle-white.svg");
  background-repeat: no-repeat;
  background-position: top center;
  background-size: contain;
}

.advantages__container {
  padding-top: 40px;
  padding-bottom: 24px;
}

.advantages__intro {
  margin: 0;
}

.advantages__content {
  padding-top: 88px;
}

.advantages__container p + p {
  margin-top: 26px;
}

.advantages__list {
  .list-reset();
  width: 260px;
  margin: 0 auto;
  text-align: center;
  background-color: @gray-light;
}

.advantages__item + .advantages__item {
  margin-top: 30px;
}

.advantages__title {
  font-size: 18px;
  font-weight: bold;
  margin-top: 0;
  margin-bottom: 13px;
  color: @black;
}

.advantages__text {
  font-weight: 400;
  margin: 0;
}

.advantages__text-tablet-space {
  display: none;
}

.advantages__images {
  position: relative;
  margin: 40px auto 0 auto;
  z-index: -1;
}

.advantages__image {
  display: block;
  width: 157px;
  height: 320px;
  margin: 0 auto;

  &--hide {
    display: none;
  }
}

@media (min-width: @tablet-width) {
  .advantages__header {
    font-size: 40px;
    line-height: 48px;
  }

  .advantages__container {
    padding-top: 50px;
    padding-bottom: 45px;
  }

  .advantages__container p + p {
    margin: 0 130px;
  }

  .advantages__content {
    display: flex;
    align-items: flex-end;
    padding-top: 0;
  }

  .advantages__image {
    width: 268px;
    height: 481px;
  }

  .advantages__images {
    margin: 5px 0 0 0;
    order: -1;
    z-index: 0;
  }

  .advantages__list {
    width: 310px;
    margin-right: 0;
    margin-top: 60px;
    margin-bottom: 40px;
    text-align: left;
  }

  .advantages__item + .advantages__item {
    margin-top: 33px;
  }

  .advantages__text-tablet-space {
    display: inline-block;
  }
}

@media (min-width: @desktop-width) {
  .advantages__header {
    font-size: 50px;
    line-height: 60px;
  }

  .advantages__container {
    padding-top: 68px;
    padding-bottom: 75px;
  }

  .advantages__container p + p {
    margin: 0 160px;
  }

  .advantages__content {
    flex-direction: column;
  }

  .advantages__images {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    width: 935px;
    margin-top: 0;
    margin-bottom: 57px;
  }

  .advantages__image {
    width: 292px;
    height: 302px;
    margin: 0;

    &--hide {
      display: block;
    }
  }

  .advantages__list {
    display: flex;
    justify-content: space-between;
    width: 880px;
    text-align: center;
    margin: 0 auto;
  }

  .advantages__item {
    width: 240px;
  }

  .advantages__item + .advantages__item {
    margin-top: 0;
  }

  .advantages__title {
    font-size: 30px;
    line-height: 30px;
    margin-bottom: 23px;
  }

  .advantages__text {
    font-size: 18px;
    line-height: 30px;
  }

  .advantages__text-tablet-space {
    display: none;
  }
}
</style>
