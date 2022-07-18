<template>
  <header class="header">
    <nav
      :class="{ 'header__nav--closed': !mobileMenuOpened }"
      class="header__nav"
    >
      <HeaderLogo />
      <MenuToggle
        :open="mobileMenuOpened"
        @open-menu="mobileMenuOpened = $event"
      />
      <HeaderMenu class="header__nav-list" />
    </nav>
  </header>
</template>

<script>
import HeaderLogo from "./HeaderLogo";
import MenuToggle from "./MenuToggle";
import HeaderMenu from "./HeaderMenu";

export default {
  name: "PageHeader",
  components: { HeaderMenu, MenuToggle, HeaderLogo },
  data: () => ({
    mobileMenuOpened: false,
  }),
};
</script>

<style lang="less" scoped>
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
