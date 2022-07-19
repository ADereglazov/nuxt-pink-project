<template>
  <div>
    <PageHeader />
    <main class="page-main">
      <h1 class="visually-hidden">
        Pink - раскрась серые будни в розовый цвет!
      </h1>
      <DownloadSection />
    </main>
    <div style="height: 200px"></div>
    <PageFooter />
  </div>
</template>

<script>
import PageHeader from "@/components/PageHeader";
import PageFooter from "@/components/PageFooter";
import DownloadSection from "@/components/IndexPage/DownloadSection";

export default {
  name: "IndexPage",
  components: { DownloadSection, PageFooter, PageHeader },
};
</script>
