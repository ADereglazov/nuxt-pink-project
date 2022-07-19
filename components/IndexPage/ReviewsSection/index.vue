<template>
  <section class="reviews">
    <h2 class="visually-hidden">Отзывы о приложении Pink</h2>
    <div class="reviews__wrapper slider container">
      <button
        class="reviews__button-left slider__button-left"
        type="button"
        aria-label="Предыдущий комментарий"
        @click="handleClickSliderButton('left')"
      >
        <svg
          class="reviews__arrow-left slider__arrow-left"
          width="22"
          height="41"
          aria-hidden="true"
          focusable="false"
        >
          <use xlink:href="~/assets/img/sprite.svg#icon-arrow-left"></use>
        </svg>
      </button>
      <button
        class="reviews__button-right slider__button-right"
        type="button"
        aria-label="Следующий комментарий"
        @click="handleClickSliderButton('right')"
      >
        <svg
          class="reviews__arrow-right slider__arrow-right"
          width="22"
          height="41"
          aria-hidden="true"
          focusable="false"
        >
          <use xlink:href="~/assets/img/sprite.svg#icon-arrow-right"></use>
        </svg>
      </button>
      <ul class="reviews__list slider__list">
        <li
          v-for="(item, index) in reviewsList"
          :key="item.authorName"
          :class="{ 'reviews__item--current': currentSlide === index }"
          class="reviews__item slider__item"
        >
          <blockquote class="reviews__item-details">
            <cite class="reviews__author-name">{{ item.authorName }}</cite>
            <span class="reviews__author-details">
              {{ item.authorDetails }}
            </span>
            <p class="reviews__text">
              {{ item.comment }}
            </p>
          </blockquote>
        </li>
      </ul>
      <ul class="reviews__toggles slider__toggles">
        <li
          v-for="(item, index) in reviewsList"
          :key="item.authorName"
          class="slider__item"
        >
          <button
            :class="{ 'slider__toggle--current': currentSlide === index }"
            :aria-label="item.label"
            class="slider__toggle"
            type="button"
            @click="currentSlide = index"
          ></button>
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
export default {
  name: "ReviewsSection",
  data: () => ({
    reviewsList: [
      {
        authorName: "Николай Петров",
        authorDetails: "25 лет, водитель трамвая",
        comment:
          "«Это приложение перевернуло мой мир и позволило по-новому взглянуть на привычные серые вещи! А еще я познакомился со своей будущей женой в комментариях к выложенной фотографии!»",
        label: "Первый слайд",
      },
      {
        authorName: "Петр Николаев",
        authorDetails: "52 года, водитель кобылы",
        comment:
          "«Это приложение ничего почти не перевернуло! Но я нашел кобылу по фотографии! Теперь я - Водитель кобылы!»",
        label: "Второй слайд",
      },
      {
        authorName: "Вася Козлодоев",
        authorDetails: "34 года, безработный",
        comment: "«Хорошее приложение! Но Angry Beards лучше!»",
        label: "Третий слайд",
      },
    ],
    currentSlide: 0,
  }),
  methods: {
    handleClickSliderButton(direction) {
      const countItems = this.reviewsList.length;

      if (direction === "left") {
        this.currentSlide = (this.currentSlide + 1) % countItems;
      } else if (direction === "right") {
        this.currentSlide = (this.currentSlide + countItems - 1) % countItems;
      }
    },
  },
};
</script>

<style lang="less" scoped>
.slider__toggles {
  .list-reset();
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 60px;
  margin: 0 auto;
}

.slider__toggle {
  display: block;
  width: 6px;
  height: 6px;
  padding: 0;
  border: 3px solid @blue-dark-opacity03;
  border-radius: 50%;

  &:hover {
    cursor: pointer;
    border-color: @blue-dark-opacity06;
  }

  &:active {
    outline: none;
    border-color: @blue-dark-opacity01;
  }

  &--current {
    width: 12px;
    height: 12px;
    border: 3px solid @blue-dark;
    background-color: transparent;

    &:hover {
      cursor: default;
      border-color: @blue-dark;
    }
  }
}

.slider__button-left,
.slider__button-right {
  display: none;
}

@media (min-width: @desktop-width) {
  .slider {
    position: relative;
  }

  .slider__button-left,
  .slider__button-right {
    position: absolute;
    top: 54%;
    display: block;
    width: 22px;
    height: 41px;
    padding: 0;
    border: none;
    background-color: @white;

    &:hover {
      cursor: pointer;
    }
  }

  .slider__button-left:hover .slider__arrow-left,
  .slider__button-right:hover .slider__arrow-right {
    fill: @blue-dark-opacity06;
  }

  .slider__button-left:active .slider__arrow-left,
  .slider__button-right:active .slider__arrow-right {
    fill: @blue-dark-opacity01;
  }

  .slider__button-right {
    right: 10px;
  }

  .slider__arrow-left,
  .slider__arrow-right {
    fill: @gray-lighter;
  }
}

.reviews {
  text-align: center;
  margin-top: -43px;
  background-color: @white;
}

.reviews__wrapper {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  min-height: 352px;
  padding-top: 42px;
  padding-bottom: 42px;
}

.reviews__item {
  display: none;

  &--current {
    display: block;
  }
}

.reviews__item-details {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin: 0;
}

.reviews__author-name {
  font-size: 18px;
  font-style: normal;
  font-weight: bold;
  line-height: 30px;
  margin-bottom: 14px;
  color: @black;
}

.reviews__author-details {
  display: none;
}

.reviews__text {
  font-weight: 400;
  line-height: 30px;
  margin-top: 0;
  margin-bottom: 14px;
}

.reviews__list {
  .list-reset();
}

@media (min-width: @tablet-width) {
  .reviews {
    padding-top: 10px;
    margin-top: 0;
  }

  .reviews__wrapper {
    min-height: 311px;
    padding-top: 62px;
    padding-bottom: 15px;
  }

  .reviews__author-name {
    font-size: 20px;
    margin-bottom: 0;
    order: 1;
  }

  .reviews__author-details {
    display: inline-block;
    vertical-align: middle;
    font-weight: 400;
    line-height: 35px;
    order: 2;
  }

  .reviews__text {
    font-size: 18px;
    margin-bottom: 35px;
  }

  .reviews__list {
    margin-bottom: 32px;
  }
}

@media (min-width: @desktop-width) {
  .reviews {
    min-height: 420px;
    padding: 0;
    background-image: url("~assets//img/bg-quotes.svg");
    background-repeat: no-repeat;
    background-position: 50% 73px;
  }

  .reviews__wrapper {
    display: block;
    min-height: auto;
    padding-top: 190px;
    padding-bottom: 20px;
  }

  .reviews__list {
    width: 695px;
    margin: 0 auto;
  }

  .reviews__author-name {
    font-size: 24px;
  }

  .reviews__author-details {
    font-size: 18px;
  }

  .reviews__text {
    margin-top: 0;
  }

  .reviews__toggles {
    display: none;
  }
}
</style>
