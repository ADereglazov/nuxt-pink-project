<template>
  <div>
    <PageHeader />
    <main class="page-main">
      <h1 class="visually-hidden">
        Pink - раскрась серые будни в розовый цвет!
      </h1>
      <DownloadSection />
      <AdvantagesSection />
      <EffectSection />
      <ReviewsSection />
      <PricesSection />
    </main>
    <PageFooter />
  </div>
</template>

<script>
import PageHeader from "@/components/PageHeader";
import PageFooter from "@/components/PageFooter";
import DownloadSection from "@/components/IndexPage/DownloadSection";
import AdvantagesSection from "@/components/IndexPage/AdvantagesSection";
import EffectSection from "@/components/IndexPage/EffectSection";
import ReviewsSection from "@/components/IndexPage/ReviewsSection";
import PricesSection from "@/components/IndexPage/PricesSection";

export default {
  name: "IndexPage",
  components: {
    PricesSection,
    ReviewsSection,
    EffectSection,
    AdvantagesSection,
    DownloadSection,
    PageFooter,
    PageHeader,
  },
};
</script>
