<template>
  <div class="social">
    <ul class="social__list">
      <li v-for="item in socialList" :key="item.name" class="social__item">
        <a class="social__link" :href="item.link" :aria-label="item.name">
          <svg
            :width="item.image.width"
            :height="item.image.height"
            class="social__image"
            role="img"
          >
            <use :xlink:href="iconSrc(item.image.iconId)"></use>
          </svg>
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
const SPRITE = require("~/assets/img/sprite.svg");

export default {
  name: "SocialsIcons",
  data: () => ({
    socialList: [
      {
        name: "Твиттер",
        link: "#",
        image: {
          width: 18,
          height: 14,
          iconId: "#icon-twitter",
        },
      },
      {
        name: "Фейсбук",
        link: "#",
        image: {
          width: 9,
          height: 18,
          iconId: "#icon-facebook",
        },
      },
      {
        name: "YouTube",
        link: "#",
        image: {
          width: 15,
          height: 13,
          iconId: "#icon-youtube",
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
