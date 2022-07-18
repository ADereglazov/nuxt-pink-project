<template>
  <div>
    <PageHeader />
  </div>
</template>

<script>
import PageHeader from "~/components/PageHeader";

export default {
  name: "IndexPage",
  components: { PageHeader },
};
</script>

<style lang="less" scoped>
.title {
  color: tomato;
}
</style>
