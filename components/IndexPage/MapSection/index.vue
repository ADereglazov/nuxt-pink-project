<template>
  <section class="map">
    <h2 class="visually-hidden">Карта проезда</h2>
    <div class="map__wrapper">
      <picture>
        <source
          type="image/webp"
          media="(min-width: 960px)"
          srcset="
            ~/assets/img/map-desktop@1x.webp 1x,
            ~/assets/img/map-desktop@2x.webp 2x
          "
        />
        <source
          type="image/webp"
          media="(min-width: 660px)"
          srcset="
            ~/assets/img/map-tablet@1x.webp 1x,
            ~/assets/img/map-tablet@2x.webp 2x
          "
        />
        <source
          type="image/webp"
          srcset="
            ~/assets/img/map-mobile@1x.webp 1x,
            ~/assets/img/map-mobile@2x.webp 2x
          "
        />
        <source
          media="(min-width: 960px)"
          srcset="
            ~/assets/img/map-desktop@1x.jpg 1x,
            ~/assets/img/map-desktop@2x.jpg 2x
          "
        />
        <source
          media="(min-width: 660px)"
          srcset="
            ~/assets/img/map-tablet@1x.jpg 1x,
            ~/assets/img/map-tablet@2x.jpg 2x
          "
        />
        <img
          class="map__image"
          src="~/assets/img/map-mobile@1x.png"
          srcset="~/assets/img/map-mobile@2x.jpg 2x"
          width="320"
          height="200"
          alt="Схема проезда"
        />
      </picture>
    </div>
    <div id="map" class="map__interactive">
      <iframe
        src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d1998.6037872533216!2d30.32085871607062!3d59.93871648187625!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x4696310fca145cc1%3A0x42b32648d8238007!2z0JHQvtC70YzRiNCw0Y8g0JrQvtC90Y7RiNC10L3QvdCw0Y8g0YPQuy4sIDE5LzgsINCh0LDQvdC60YIt0J_QtdGC0LXRgNCx0YPRgNCzLCAxOTExODY!5e0!3m2!1sru!2sru!4v1610353206456!5m2!1sru!2sru"
        width="100%"
        height="100%"
        style="border: 0"
        allowfullscreen=""
        aria-hidden="false"
        tabindex="0"
      ></iframe>
    </div>
  </section>
</template>

<script>
export default {
  name: "MapSection",
};
</script>

<style lang="less" scoped>
.map {
  position: relative;

  &::before {
    content: "";
    position: absolute;
    top: -2px;
    width: 100%;
    height: 100%;
    background-image: url("~assets/img/bg-triangle-white-footer.svg");
    background-repeat: no-repeat;
    background-position: top center;
    background-size: contain;
    z-index: 5;
    pointer-events: none;
  }
}

.map__wrapper {
  width: @mobile-width;
  height: 200px;
  margin-left: auto;
  margin-right: auto;
}

.map__image {
  display: block;
  width: auto;
  height: 100%;
}

.map__interactive {
  position: absolute;
  top: 0;
  min-width: @mobile-width;
  width: 100%;
  height: 200px;
  z-index: 1;
}

@media (min-width: @tablet-width) {
  .map__wrapper {
    width: @tablet-width;
    height: 377px;
  }

  .map__interactive {
    min-width: @tablet-width;
    height: 377px;
  }
}

@media (min-width: @desktop-width) {
  .map__wrapper {
    width: @desktop-width;
    height: 505px;
  }

  .map__interactive {
    min-width: @desktop-width;
    height: 505px;
  }
}
</style>
