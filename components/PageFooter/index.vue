<template>
  <footer
    :class="{ 'page-footer--hide': $route.path === '/' }"
    class="page-footer"
  >
    <div class="page-footer__wrapper container">
      <FooterLogo />
      <SocialsIcons />
      <CopyRight />
    </div>
  </footer>
</template>

<script>
import FooterLogo from "./FooterLogo";
import SocialsIcons from "./SocialsIcons";
import CopyRight from "./CopyRight";

export default {
  name: "PageFooter",
  components: { CopyRight, SocialsIcons, FooterLogo },
};
</script>

<style lang="less" scoped>
.page-footer {
  min-height: 285px;
  padding-top: 40px;
  background-color: @white;

  &--hide {
    display: none;
  }

  @media (min-width: @tablet-width) {
    display: block;
    min-height: 127px;
    padding-top: 45px;
  }

  @media (min-width: @desktop-width) {
    min-height: 197px;
    padding-top: 77px;
  }

  &__wrapper {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    min-height: 205px;

    @media (min-width: @tablet-width) {
      flex-direction: row;
      justify-content: space-between;
      min-height: 46px;
    }
  }
}
</style>
