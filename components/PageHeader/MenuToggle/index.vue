<template>
  <button
    class="toggle"
    type="button"
    aria-label="Переключить меню"
    @click="handleClick"
  >
    <svg
      v-show="open"
      class="toggle-image"
      width="24"
      height="24"
      aria-hidden="true"
      focusable="false"
    >
      <use xlink:href="~/assets/img/sprite.svg#icon-menu-cross"></use>
    </svg>
    <svg
      v-show="!open"
      class="toggle-image"
      width="50"
      height="24"
      aria-hidden="true"
      focusable="false"
    >
      <use xlink:href="~/assets/img/sprite.svg#icon-menu-burger"></use>
    </svg>
  </button>
</template>

<script>
export default {
  name: "MenuToggle",
  props: {
    open: {
      type: Boolean,
      required: true,
      default: false,
    },
  },
  methods: {
    handleClick() {
      this.$emit("open-menu", !this.open);
    },
  },
};
</script>

<style lang="less" scoped>
.toggle {
  @media (max-width: @mobile-width-only) {
    position: absolute;
    right: 20px;
    top: 22px;
    display: block;
    height: 24px;
    padding: 0;
    border: none;
    background-color: transparent;

    &:hover {
      cursor: pointer;
    }

    &:hover &-image {
      color: @pink;
    }

    &:active &-image {
      color: @pink;
    }

    &-image {
      color: @white;
    }
  }

  @media (min-width: @tablet-width) {
    top: 45px;
  }

  @media (min-width: @desktop-width) {
    display: none;
  }
}
</style>
