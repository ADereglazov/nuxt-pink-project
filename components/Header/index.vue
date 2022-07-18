<template>
  <header class="header">
    <nav :class="{ 'header__nav--closed': !mobileMenuOpened }" class="header__nav">
      <Logo />
      <MenuToggle :open="mobileMenuOpened" @open-menu="mobileMenuOpened = $event" />
      <Menu class="header__nav-list" />
    </nav>
  </header>
</template>

<script>
import Logo from "./Logo";
import MenuToggle from "./MenuToggle";
import Menu from "./Menu";

export default {
  name: 'Header',
  components: { Menu, MenuToggle, Logo },
  data: () => ({
    mobileMenuOpened: false
  })
}
</script>

<style lang="less" scoped>
@import (reference) "./assets/styles/styles.less";

.header {
  position: relative;
  min-height: 66px;
  margin-bottom: -66px;
  background-color: @black-opacity03;
  z-index: 1;

  @media (max-width: @mobile-width-only) {
    &__nav--closed &__nav-list {
      display: none;
    }
  }

  @media (min-width: @tablet-width) {
    min-height: 110px;
    margin-bottom: -110px;
  }

  @media (min-width: @desktop-width) {
    &__nav {
      display: flex;
      justify-content: space-between;
      min-height: 110px;
      width: @desktop-width;
      padding-right: 10px;
      padding-left: 10px;
      margin-right: auto;
      margin-left: auto;
      background-color: transparent;
    }
  }
}
</style>
