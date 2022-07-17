<template>
  <ul class="menu">
    <li
      v-for="(item, index) in items"
      :key="index"
      :class="{ 'menu-item--first': index === 0 }"
      class="menu-item"
    >
      <template v-if="item.name">
        <a v-if="item.name && item.link.includes('https://')"
           :href="item.link"
           class="menu-link"
        >
          {{ item.name }}
        </a>

        <nuxt-link
          v-else
          :to="item.link"
          class="menu-link"
        >
          {{ item.name }}
        </nuxt-link>
      </template>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'Menu',
  data: () => ({
    items: [
        { name: '', link: '' },
        { name: 'Главная', link: '' },
        { name: 'Фотографии', link: '' },
        { name: 'Конкурс', link: '' },
        { name: 'HTML Academy', link: 'https://htmlacademy.ru/intensive/adaptive' }
      ]
  })
}
</script>

<style lang="less" scoped>
@import (reference) "./assets/styles/styles.less";

.menu {
  .list-reset();
  font-size: 18px;
  font-weight: bold;
  line-height: 32px;
  text-align: center;
  text-transform: uppercase;

  @media (max-width: @mobile-width-only) {
    background-color: @blue-dark;
  }

  @media (min-width: @desktop-width) {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    width: 622px;
    margin-top: 35px;
    background-color: transparent;
    font-weight: 400;
    line-height: 40px;
    text-transform: inherit;
  }

  &-item {
    &--first {
      height: 72px;
      background-color: @blue-dark;
    }

    &--active {
      box-shadow: inset 0 1px @black;
    }

    @media (min-width: @tablet-width) {
      &--first {
        height: 110px;
      }
    }

    @media (min-width: @desktop-width) {
      & + & {
        margin-left: 5px;
      }

      &:nth-child(2) {
        margin: 0;
      }

      &--first {
        display: none;
      }

      &--active {
        box-shadow: none;
      }
    }
  }

  &-link {
    display: block;
    width: 100%;
    min-height: 64px;
    padding-top: 17px;
    text-decoration: none;
    color: @white;
    border-bottom: 1px solid transparent;
    box-shadow: inset 0 1px rgba(255, 255, 255, 0.15);

    &:hover {
      color: @pink;
    }

    &:active {
      color: @pink-opacity03;
    }

    &--current {
      cursor: default;

      &:hover {
        color: @white;
      }
    }

    @media (min-width: @desktop-width) {
      min-height: 40px;
      padding: 0;
      box-shadow: none;

      &:active {
        color: @white-opacity03;
      }

      &--current {
        border-bottom: 2px solid @white;
      }

      &--index {
        border: none;
      }
    }
  }
}
</style>
