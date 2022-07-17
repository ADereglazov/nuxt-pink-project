<template>
  <div>
    <Header />
  </div>
</template>

<script>
import Header from "~/components/Header";

export default {
  name: 'IndexPage',
  components: { Header }
}
</script>

<style lang="less" scoped>
  .title {
    color: tomato;
  }
</style>
