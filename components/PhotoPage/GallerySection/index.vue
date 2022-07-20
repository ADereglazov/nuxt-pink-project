<template>
  <section class="gallery">
    <div class="gallery__wrapper container">
      <h2 class="gallery__title">
        Взгляните на фотографии, которые выкладывают пользователи! Видите, как
        не хватает ваших?
      </h2>
      <ul class="gallery__list-comments">
        <li class="gallery__users-comment comment">
          <a
            class="comment__link comment__link--first"
            href="#"
            aria-label="Панорама дня"
          >
            <picture>
              <source
                type="image/webp"
                media="(min-width: 960px)"
                srcset="
                  ~/assets/img/panorama-desktop@1x.webp 1x,
                  ~/assets/img/panorama-desktop@2x.webp 2x
                "
              />
              <source
                type="image/webp"
                media="(min-width: 660px)"
                srcset="
                  ~/assets/img/panorama-tablet@1x.webp 1x,
                  ~/assets/img/panorama-tablet@2x.webp 2x
                "
              />
              <source
                type="image/webp"
                srcset="
                  ~/assets/img/panorama-mobile@1x.webp 1x,
                  ~/assets/img/panorama-mobile@2x.webp 2x
                "
              />
              <source
                media="(min-width: 960px)"
                srcset="
                  ~/assets/img/panorama-desktop@1x.jpg 1x,
                  ~/assets/img/panorama-desktop@2x.jpg 2x
                "
              />
              <source
                media="(min-width: 660px)"
                srcset="
                  ~/assets/img/panorama-tablet@1x.jpg 1x,
                  ~/assets/img/panorama-tablet@2x.jpg 2x
                "
              />
              <img
                class="comment__photo comment__photo--panorama"
                src="~/assets/img/panorama-mobile@1x.jpg"
                srcset="~/assets/img/panorama-mobile@2x.jpg 2x"
                width="320"
                height="137"
                alt="Панорама дня"
              />
            </picture>
            <span class="comment__panorama-label">Панорама дня</span>
          </a>
          <div class="comment__wrapper comment__wrapper--first">
            <div class="comment__user">
              <b class="comment__username">Анна</b>
              <span class="comment__time">(5 минут назад)</span>
            </div>
            <p class="comment__text comment__text--first">
              Прыгать или нет? Напишите в комментарии свой совет и смотрите
              прямую трансляцию в перископе, задавайте свои вопросы!
            </p>
            <div class="comment__like comment__like--first">
              <button
                class="comment__button"
                type="button"
                value="1"
                aria-label="Лайк"
              >
                <svg
                  class="comment__like-image"
                  width="13"
                  height="12"
                  role="img"
                >
                  <use xlink:href="~/assets/img/sprite.svg#icon-heart"></use>
                </svg>
              </button>
              <span class="comment__like-text">Нравится:</span>
              <span class="comment__like-counter">215</span>
            </div>
          </div>
        </li>
        <li class="gallery__users-comment comment">
          <a class="comment__link" href="#" aria-label="Фото">
            <picture>
              <source
                type="image/webp"
                media="(min-width: 960px)"
                srcset="
                  ~/assets/img/photo-car-desktop@1x.webp 1x,
                  ~/assets/img/photo-car-desktop@2x.webp 2x
                "
              />
              <source
                type="image/webp"
                media="(min-width: 660px)"
                srcset="
                  ~/assets/img/photo-car-tablet@1x.webp 1x,
                  ~/assets/img/photo-car-tablet@2x.webp 2x
                "
              />
              <source
                type="image/webp"
                srcset="
                  ~/assets/img/photo-car-mobile@1x.webp 1x,
                  ~/assets/img/photo-car-mobile@2x.webp 2x
                "
              />
              <source
                media="(min-width: 960px)"
                srcset="
                  ~/assets/img/photo-car-desktop@1x.jpg 1x,
                  ~/assets/img/photo-car-desktop@2x.jpg 2x
                "
              />
              <source
                media="(min-width: 660px)"
                srcset="
                  ~/assets/img/photo-car-tablet@1x.jpg 1x,
                  ~/assets/img/photo-car-tablet@2x.jpg 2x
                "
              />
              <img
                class="comment__photo"
                src="~/assets/img/photo-car-mobile@1x.jpg"
                srcset="~/assets/img/photo-car-mobile@2x.jpg 2x"
                width="280"
                height="180"
                alt="Фото"
              />
            </picture>
          </a>
          <div class="comment__wrapper">
            <div class="comment__user">
              <b class="comment__username">Левон</b>
              <span class="comment__time">(5 часов назад)</span>
            </div>
            <p class="comment__text">
              Вчера он на луну летал, сегодня в руки к нам попал.
            </p>
            <div class="comment__like">
              <button
                class="comment__button"
                type="button"
                value="1"
                aria-label="Лайк"
              >
                <svg
                  class="comment__like-image"
                  width="13"
                  height="12"
                  role="img"
                >
                  <use xlink:href="~/assets/img/sprite.svg#icon-heart"></use>
                </svg>
              </button>
              <span class="comment__like-text">Нравится:</span>
              <span class="comment__like-counter">356</span>
            </div>
          </div>
        </li>
        <li class="gallery__users-comment comment">
          <a class="comment__link" href="#" aria-label="Фото">
            <picture>
              <source
                type="image/webp"
                media="(min-width: 960px)"
                srcset="
                  ~/assets/img/photo-drumset-desktop@1x.webp 1x,
                  ~/assets/img/photo-drumset-desktop@2x.webp 2x
                "
              />
              <source
                type="image/webp"
                media="(min-width: 660px)"
                srcset="
                  ~/assets/img/photo-drumset-tablet@1x.webp 1x,
                  ~/assets/img/photo-drumset-tablet@2x.webp 2x
                "
              />
              <source
                type="image/webp"
                srcset="
                  ~/assets/img/photo-drumset-mobile@1x.webp 1x,
                  ~/assets/img/photo-drumset-mobile@2x.webp 2x
                "
              />
              <source
                media="(min-width: 960px)"
                srcset="
                  ~/assets/img/photo-drumset-desktop@1x.jpg 1x,
                  ~/assets/img/photo-drumset-desktop@2x.jpg 2x
                "
              />
              <source
                media="(min-width: 660px)"
                srcset="
                  ~/assets/img/photo-drumset-tablet@1x.jpg 1x,
                  ~/assets/img/photo-drumset-tablet@2x.jpg 2x
                "
              />
              <img
                class="comment__photo"
                src="~/assets/img/photo-drumset-mobile@1x.jpg"
                srcset="~/assets/img/photo-drumset-mobile@2x.jpg 2x"
                width="280"
                height="180"
                alt="Фото"
              />
            </picture>
          </a>
          <div class="comment__wrapper">
            <div class="comment__user">
              <b class="comment__username">Антон</b>
              <span class="comment__time">(12 часов назад)</span>
            </div>
            <p class="comment__text">Соседи будут рады!</p>
            <div class="comment__like">
              <button
                class="comment__button"
                type="button"
                value="1"
                aria-label="Лайк"
              >
                <svg
                  class="comment__like-image"
                  width="13"
                  height="12"
                  role="img"
                >
                  <use xlink:href="~/assets/img/sprite.svg#icon-heart"></use>
                </svg>
              </button>
              <span class="comment__like-text">Нравится:</span>
              <span class="comment__like-counter">666</span>
            </div>
          </div>
        </li>
        <li class="gallery__users-comment comment">
          <a class="comment__link" href="#" aria-label="Фото">
            <picture>
              <source
                type="image/webp"
                media="(min-width: 960px)"
                srcset="
                  ~/assets/img/photo-window-desktop@1x.webp 1x,
                  ~/assets/img/photo-window-desktop@2x.webp 2x
                "
              />
              <source
                type="image/webp"
                media="(min-width: 660px)"
                srcset="
                  ~/assets/img/photo-window-tablet@1x.webp 1x,
                  ~/assets/img/photo-window-tablet@2x.webp 2x
                "
              />
              <source
                type="image/webp"
                srcset="
                  ~/assets/img/photo-window-mobile@1x.webp 1x,
                  ~/assets/img/photo-window-mobile@2x.webp 2x
                "
              />
              <source
                media="(min-width: 960px)"
                srcset="
                  ~/assets/img/photo-window-desktop@1x.jpg 1x,
                  ~/assets/img/photo-window-desktop@2x.jpg 2x
                "
              />
              <source
                media="(min-width: 660px)"
                srcset="
                  ~/assets/img/photo-window-tablet@1x.jpg 1x,
                  ~/assets/img/photo-window-tablet@2x.jpg 2x
                "
              />
              <img
                class="comment__photo"
                src="~/assets/img/photo-window-mobile@1x.jpg"
                srcset="~/assets/img/photo-window-mobile@2x.jpg 2x"
                width="280"
                height="180"
                alt="Фото"
              />
            </picture>
          </a>
          <div class="comment__wrapper">
            <div class="comment__user">
              <b class="comment__username">Борис</b>
              <span class="comment__time">(20 часов назад)</span>
            </div>
            <p class="comment__text">
              Здесь могла быть ваша цитата о высоком и вечном.
            </p>
            <div class="comment__like">
              <button
                class="comment__button"
                type="button"
                value="1"
                aria-label="Лайк"
              >
                <svg
                  class="comment__like-image"
                  width="13"
                  height="12"
                  role="img"
                >
                  <use xlink:href="~/assets/img/sprite.svg#icon-heart"></use>
                </svg>
              </button>
              <span class="comment__like-text">Нравится:</span>
              <span class="comment__like-counter">215</span>
            </div>
          </div>
        </li>
        <li class="gallery__users-comment comment">
          <a class="comment__link" href="#" aria-label="Фото">
            <picture>
              <source
                type="image/webp"
                media="(min-width: 960px)"
                srcset="
                  ~/assets/img/photo-fair-desktop@1x.webp 1x,
                  ~/assets/img/photo-fair-desktop@2x.webp 2x
                "
              />
              <source
                type="image/webp"
                media="(min-width: 660px)"
                srcset="
                  ~/assets/img/photo-fair-tablet@1x.webp 1x,
                  ~/assets/img/photo-fair-tablet@2x.webp 2x
                "
              />
              <source
                type="image/webp"
                srcset="
                  ~/assets/img/photo-fair-mobile@1x.webp 1x,
                  ~/assets/img/photo-fair-mobile@2x.webp 2x
                "
              />
              <source
                media="(min-width: 960px)"
                srcset="
                  ~/assets/img/photo-fair-desktop@1x.jpg 1x,
                  ~/assets/img/photo-fair-desktop@2x.jpg 2x
                "
              />
              <source
                media="(min-width: 660px)"
                srcset="
                  ~/assets/img/photo-fair-tablet@1x.jpg 1x,
                  ~/assets/img/photo-fair-tablet@2x.jpg 2x
                "
              />
              <img
                class="comment__photo"
                src="~/assets/img/photo-fair-mobile@1x.jpg"
                srcset="~/assets/img/photo-fair-mobile@2x.jpg 2x"
                width="280"
                height="180"
                alt="Фото"
              />
            </picture>
          </a>
          <div class="comment__wrapper">
            <div class="comment__user">
              <b class="comment__username">Сергей</b>
              <span class="comment__time">(25 часов назад)</span>
            </div>
            <p class="comment__text">Самая кубанская в мире!</p>
            <div class="comment__like">
              <button
                class="comment__button"
                type="button"
                value="1"
                aria-label="Лайк"
              >
                <svg
                  class="comment__like-image"
                  width="13"
                  height="12"
                  role="img"
                >
                  <use xlink:href="~/assets/img/sprite.svg#icon-heart"></use>
                </svg>
              </button>
              <span class="comment__like-text">Нравится:</span>
              <span class="comment__like-counter">4</span>
            </div>
          </div>
        </li>
        <li class="gallery__users-comment comment">
          <a class="comment__link" href="#" aria-label="Фото">
            <picture>
              <source
                type="image/webp"
                media="(min-width: 960px)"
                srcset="
                  ~/assets/img/photo-pov-desktop@1x.webp 1x,
                  ~/assets/img/photo-pov-desktop@2x.webp 2x
                "
              />
              <source
                type="image/webp"
                media="(min-width: 660px)"
                srcset="
                  ~/assets/img/photo-pov-tablet@1x.webp 1x,
                  ~/assets/img/photo-pov-tablet@2x.webp 2x
                "
              />
              <source
                type="image/webp"
                srcset="
                  ~/assets/img/photo-pov-mobile@1x.webp 1x,
                  ~/assets/img/photo-pov-mobile@2x.webp 2x
                "
              />
              <source
                media="(min-width: 960px)"
                srcset="
                  ~/assets/img/photo-pov-desktop@1x.jpg 1x,
                  ~/assets/img/photo-pov-desktop@2x.jpg 2x
                "
              />
              <source
                media="(min-width: 660px)"
                srcset="
                  ~/assets/img/photo-pov-tablet@1x.jpg 1x,
                  ~/assets/img/photo-pov-tablet@2x.jpg 2x
                "
              />
              <img
                class="comment__photo"
                src="~/assets/img/photo-pov-mobile@1x.jpg"
                srcset="~/assets/img/photo-pov-mobile@2x.jpg 2x"
                width="280"
                height="180"
                alt="Фото"
              />
            </picture>
          </a>
          <div class="comment__wrapper">
            <div class="comment__user">
              <b class="comment__username">Максим</b>
              <span class="comment__time">(40 часов назад)</span>
            </div>
            <p class="comment__text">Где снег-то?</p>
            <div class="comment__like">
              <button
                class="comment__button"
                type="button"
                value="1"
                aria-label="Лайк"
              >
                <svg
                  class="comment__like-image"
                  width="13"
                  height="12"
                  role="img"
                >
                  <use xlink:href="~/assets/img/sprite.svg#icon-heart"></use>
                </svg>
              </button>
              <span class="comment__like-text">Нравится:</span>
              <span class="comment__like-counter">150</span>
            </div>
          </div>
        </li>
        <li class="gallery__users-comment comment">
          <a class="comment__link" href="#" aria-label="Фото">
            <picture>
              <source
                type="image/webp"
                media="(min-width: 960px)"
                srcset="
                  ~/assets/img/photo-wing-desktop@1x.webp 1x,
                  ~/assets/img/photo-wing-desktop@2x.webp 2x
                "
              />
              <source
                type="image/webp"
                media="(min-width: 660px)"
                srcset="
                  ~/assets/img/photo-wing-tablet@1x.webp 1x,
                  ~/assets/img/photo-wing-tablet@2x.webp 2x
                "
              />
              <source
                type="image/webp"
                srcset="
                  ~/assets/img/photo-wing-mobile@1x.webp 1x,
                  ~/assets/img/photo-wing-mobile@2x.webp 2x
                "
              />
              <source
                media="(min-width: 960px)"
                srcset="
                  ~/assets/img/photo-wing-desktop@1x.jpg 1x,
                  ~/assets/img/photo-wing-desktop@2x.jpg 2x
                "
              />
              <source
                media="(min-width: 660px)"
                srcset="
                  ~/assets/img/photo-wing-tablet@1x.jpg 1x,
                  ~/assets/img/photo-wing-tablet@2x.jpg 2x
                "
              />
              <img
                class="comment__photo"
                src="~/assets/img/photo-wing-mobile@1x.jpg"
                srcset="~/assets/img/photo-wing-mobile@2x.jpg 2x"
                width="280"
                height="180"
                alt="Фото"
              />
            </picture>
          </a>
          <div class="comment__wrapper">
            <div class="comment__user">
              <b class="comment__username">Надежда</b>
              <span class="comment__time">(45 часов назад)</span>
            </div>
            <p class="comment__text">Всем GM и взаимные лайки!</p>
            <div class="comment__like">
              <button
                class="comment__button"
                type="button"
                value="1"
                aria-label="Лайк"
              >
                <svg
                  class="comment__like-image"
                  width="13"
                  height="12"
                  role="img"
                >
                  <use xlink:href="~/assets/img/sprite.svg#icon-heart"></use>
                </svg>
              </button>
              <span class="comment__like-text">Нравится:</span>
              <span class="comment__like-counter">2560</span>
            </div>
          </div>
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
export default {
  name: "GallerySection",
};
</script>

<style lang="less" scoped>
@import "./assets/styles/comment.less";

.gallery {
  position: relative;
  overflow: hidden;
  background-color: @white;
}

.gallery__title {
  min-height: 185px;
  font-size: 14px;
  font-weight: 400;
  line-height: 30px;
  text-align: center;
  padding: 45px 15px 20px 15px;
  margin: 0;
}

.gallery__list-comments {
  .list-reset();
  display: flex;
  flex-direction: column;
}

.gallery__users-comment + .gallery__users-comment {
  margin-top: 22px;
}

@media (min-width: @tablet-width) {
  .gallery__title {
    min-height: 228px;
    font-size: 18px;
    padding: 92px 90px 20px 90px;
  }

  .gallery__list-comments {
    flex-direction: row;
    flex-wrap: wrap;
  }

  .gallery__users-comment + .gallery__users-comment {
    margin-top: 0;
  }

  .gallery__users-comment:first-child {
    width: 100%;
    margin-bottom: 50px;
  }

  @media (max-width: @mobile-width-only) {
    .gallery__users-comment:nth-child(n + 4) {
      margin-top: 20px;
    }

    .gallery__users-comment:nth-child(2n + 3) {
      margin-left: 20px;
    }
  }
}

@media (min-width: @desktop-width) {
  .gallery__title {
    min-height: 240px;
    font-size: 18px;
    padding: 91px 180px 20px 180px;
  }

  .gallery__users-comment:nth-child(n + 5) {
    margin-top: 54px;
  }

  .gallery__users-comment:nth-child(3n + 3) {
    margin-right: 20px;
    margin-left: 20px;
  }
}
</style>
