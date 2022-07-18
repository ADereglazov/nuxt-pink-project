<template>
  <div>
    <PageHeader />
    <div style="height: 200px"></div>
    <PageFooter />
  </div>
</template>

<script>
import PageHeader from "@/components/PageHeader";
import PageFooter from "@/components/PageFooter";

export default {
  name: "IndexPage",
  components: { PageFooter, PageHeader },
};
</script>
