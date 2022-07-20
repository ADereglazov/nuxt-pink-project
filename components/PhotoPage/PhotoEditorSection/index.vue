<template>
  <section class="photoeditor">
    <h2 class="visually-hidden">Редактор фото для загрузки на сайт</h2>
    <header class="photoeditor__header">
      <div class="photoeditor__wrapper-text container">
        <p class="photoeditor__title">
          Затмите их всех!<br />
          Выкладывайте все, что накопилось в телефоне!
        </p>
      </div>
    </header>
    <div class="photoeditor__wrapper container">
      <form
        class="photoeditor__form"
        action="https://echo.htmlacademy.ru"
        method="post"
      >
        <picture>
          <source
            type="image/webp"
            media="(min-width: 960px)"
            srcset="
              ~/assets/img/photo-road-desktop@1x.webp 1x,
              ~/assets/img/photo-road-desktop@2x.webp 2x
            "
          />
          <source
            type="image/webp"
            media="(min-width: 660px)"
            srcset="
              ~/assets/img/photo-road-tablet@1x.webp 1x,
              ~/assets/img/photo-road-tablet@2x.webp 2x
            "
          />
          <source
            type="image/webp"
            srcset="
              ~/assets/img/photo-road-mobile@1x.webp 1x,
              ~/assets/img/photo-road-mobile@2x.webp 2x
            "
          />
          <source
            media="(min-width: 960px)"
            srcset="
              ~/assets/img/photo-road-desktop@1x.jpg 1x,
              ~/assets/img/photo-road-desktop@2x.jpg 2x
            "
          />
          <source
            media="(min-width: 660px)"
            srcset="
              ~/assets/img/photo-road-tablet@1x.jpg 1x,
              ~/assets/img/photo-road-tablet@2x.jpg 2x
            "
          />
          <img
            class="photoeditor__photo"
            src="~/assets/img/photo-road-mobile@1x.jpg"
            srcset="~/assets/img/photo-road-mobile@2x.jpg 2x"
            width="280"
            height="374"
            alt="Редактируемое фото"
          />
        </picture>
        <div class="photoeditor__tools">
          <div class="photoeditor__wrapper-buttons-tools">
            <button
              v-for="(button, index) in tools"
              :key="button.button.name"
              :class="{
                'photoeditor__button-tool--current': toolCurrent === index,
              }"
              class="photoeditor__button-tool"
              type="button"
              :aria-label="button.button.name"
              @click="toolCurrent = index"
            >
              <svg
                class="photoeditor__icon-tool"
                :width="button.button.width"
                :height="button.button.height"
                aria-hidden="true"
                focusable="false"
              >
                <use :xlink:href="iconSrc(button.button.iconId)"></use>
              </svg>
            </button>
          </div>
          <div class="photoeditor__wrapper-inputs">
            <label
              v-for="(input, index) in tools"
              :key="input.range.name"
              :class="{
                'photoeditor__label--hide': toolCurrent !== index,
              }"
              class="photoeditor__label"
              tabindex="0"
              :aria-label="input.range.name"
            >
              <input
                class="photoeditor__range visually-hidden"
                type="range"
                tabindex="-1"
                min="1"
                max="100"
                :value="input.range.value"
              />
            </label>
          </div>
          <div class="photoeditor__buttons">
            <button class="photoeditor__button" type="submit">Запостить</button>
            <button
              class="photoeditor__button photoeditor__button--reset"
              type="reset"
            >
              Отмена
            </button>
          </div>
        </div>
      </form>
    </div>
  </section>
</template>

<script>
const SPRITE = require("~/assets/img/sprite.svg");

export default {
  name: "PhotoEditorSection",
  data: () => ({
    tools: [
      {
        button: {
          name: "Обрезка",
          width: 44,
          height: 44,
          iconId: "#icon-editor-crop",
        },
        range: {
          name: "Регулировка обрезки",
          value: 80,
        },
      },
      {
        button: {
          name: "Заливка",
          width: 44,
          height: 44,
          iconId: "#icon-editor-fill",
        },
        range: {
          name: "Регулировка заливки",
          value: 50,
        },
      },
      {
        button: {
          name: "Контраст",
          width: 32,
          height: 32,
          iconId: "#icon-editor-contrast",
        },
        range: {
          name: "Регулировка контраста",
          value: 20,
        },
      },
    ],
    toolCurrent: 0,
  }),
  methods: {
    iconSrc(id) {
      return SPRITE + id;
    },
  },
};
</script>

<style lang="less" scoped>
.photoeditor__header {
  position: relative;
  min-height: 175px;
  background-color: @white;

  &::before {
    content: "";
    position: absolute;
    bottom: -555px;
    width: 100%;
    height: 1px;
    background-color: @gray-dark;
  }
}

.photoeditor__title {
  font-weight: 400;
  line-height: 30px;
  text-align: center;
  padding-top: 45px;
  padding-bottom: 20px;
  margin: 0;
}

.photoeditor__button {
  display: block;
  width: 280px;
  min-height: 55px;
  font-size: 18px;
  font-weight: 700;
  color: @pink;
  background-color: @gray-light;
  padding-top: 5px;
  padding-bottom: 5px;
  border: 3px solid @pink;
  border-radius: 27px;

  &:hover {
    cursor: pointer;
    color: @white;
    background-color: @pink;
  }

  &:active {
    outline: none;
    color: @white-opacity03;
    background-color: @pink;
  }

  &--reset {
    color: @gray-dark;
    background-color: @gray-light;
    border-color: @gray-dark;

    &:hover {
      color: @gray-darken;
      background-color: @gray-light;
      border-color: @gray-darken;
    }

    &:active {
      color: @white-opacity03;
      background-color: @gray-darken;
      border-color: @gray-darken;
    }
  }
}

.photoeditor__button + .photoeditor__button {
  margin-top: 12px;
}

.photoeditor__wrapper {
  min-height: 760px;
  padding-top: 20px;
  padding-bottom: 40px;
}

.photoeditor__photo {
  display: block;
  width: 280px;
  height: auto;
}

.photoeditor__range + .photoeditor__range {
  display: none;
}

.photoeditor__wrapper-buttons-tools {
  display: flex;
  justify-content: space-between;
  width: 208px;
  margin: 40px auto;
}

.photoeditor__button-tool {
  width: 48px;
  height: 44px;
  padding: 0;
  border: 0;
  background-color: transparent;

  &:hover {
    cursor: pointer;
  }

  &--current:hover {
    cursor: default;
  }
}

.photoeditor__icon-tool {
  display: block;
  margin: 0 auto;
  fill: @blue-dark-opacity03;

  &:hover {
    fill: @blue-dark-opacity06;
  }
}

.photoeditor__button-tool--current .photoeditor__icon-tool {
  fill: @pink;
}

.photoeditor__wrapper-inputs {
  margin-bottom: 73px;
}

.photoeditor__label {
  position: relative;
  display: block;
  width: 240px;
  height: 2px;
  background-color: @blue-dark;
  margin: 0 auto;

  &:hover {
    cursor: pointer;
  }

  &::before {
    content: "";
    position: absolute;
    transform: translateY(-45%);
    display: block;
    width: 15px;
    height: 15px;
    border: 2px solid @pink;
    border-radius: 50%;
    background-color: @white;
  }

  &:first-child::before {
    right: 35px;
  }

  &:nth-child(2)::before {
    left: 22px;
  }

  &:last-child::before {
    left: 93px;
  }

  &:active::before {
    background-color: @pink;
  }

  &--hide {
    display: none;
  }
}

@media (min-width: @tablet-width) {
  .photoeditor__header {
    min-height: 194px;

    &::before {
      display: none;
    }
  }

  .photoeditor__title {
    font-size: 18px;
    padding-top: 65px;
  }

  .photoeditor__wrapper {
    min-height: 510px;
    padding-top: 56px;
    padding-bottom: 54px;
  }

  .photoeditor__form {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    min-height: 400px;
  }

  .photoeditor__photo {
    width: 300px;
  }

  .photoeditor__tools {
    position: relative;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    width: 260px;
    min-height: 400px;
    margin-right: 15px;

    &::before {
      content: "";
      position: absolute;
      top: 55px;
      left: 0;
      width: 275px;
      height: 1px;
      background-color: @gray-dark;
      box-shadow: 0 74px @gray-dark, 0 144px @gray-dark;
    }
  }

  .photoeditor__button-tool:hover {
    cursor: default;
  }

  @media (max-width: @mobile-width-only) {
    .photoeditor__button-tool {
      width: 24px;
      height: 22px;

      &:first-child .photoeditor__icon-tool {
        width: 22px;
        height: 22px;
      }

      &:nth-child(2) .photoeditor__icon-tool {
        width: 24px;
        height: 22px;
      }

      &:last-child .photoeditor__icon-tool {
        width: 16px;
        height: 16px;
      }
    }
  }

  .photoeditor__label {
    width: 200px;

    &--hide {
      display: block;
    }

    &:first-child::before {
      right: 40px;
    }
  }

  .photoeditor__icon-tool {
    fill: @pink;

    &:hover {
      fill: @pink;
    }
  }

  .photoeditor__separator {
    display: none;
  }

  .photoeditor__range + .photoeditor__range {
    display: inherit;
  }

  .photoeditor__wrapper-buttons-tools {
    flex-direction: column;
    align-items: center;
    width: 24px;
    height: 165px;
    padding: 0;
    margin: 10px 0 40px 2px;
  }

  .photoeditor__wrapper-inputs {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 145px;
    margin-top: 19px;
    margin-right: 3px;
    margin-bottom: 0;
  }

  .photoeditor__buttons {
    margin-top: auto;
  }

  .photoeditor__button {
    width: 260px;
  }

  .photoeditor__button + .photoeditor__button {
    margin-top: 24px;
  }
}

@media (min-width: @desktop-width) {
  .photoeditor {
    padding-bottom: 28px;
    background-color: @white;
  }

  .photoeditor__header {
    min-height: 185px;
  }

  .photoeditor__wrapper {
    padding: 0;
  }

  .photoeditor__title {
    padding-top: 58px;
  }

  .photoeditor__form {
    width: 940px;
    padding: 57px 0;
    margin: 0 auto;
    background-color: @gray-light;
  }

  .photoeditor__photo {
    margin-left: 80px;
  }

  .photoeditor__wrapper-buttons-tools {
    width: 48px;
    height: 186px;
    margin: 0 0 40px 0;
  }

  .photoeditor__tools {
    width: 410px;
    margin-right: 60px;

    &::before {
      width: 410px;
    }
  }

  .photoeditor__wrapper-inputs {
    margin-right: 30px;
  }

  .photoeditor__label {
    width: 288px;

    &::before {
      left: 70px;
    }

    &:nth-child(2)::before {
      left: 246px;
    }

    &:last-child::before {
      left: 160px;
    }
  }

  .photoeditor__buttons {
    display: flex;
    flex-wrap: wrap;
    align-items: flex-end;
  }

  .photoeditor__button + .photoeditor__button {
    margin-top: 0;
  }

  .photoeditor__button {
    width: 183px;

    &:nth-child(even) {
      margin-top: 0;
      margin-left: 44px;
    }

    &:nth-child(n + 3) {
      margin-top: 10px;
    }
  }
}
</style>
