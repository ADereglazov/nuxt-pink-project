<template>
  <div>
    <PageHeader />
    <main class="page-main">
      <h1 class="visually-hidden">Конкурс от Pink</h1>
      <ChallengeSection />
      <FormSection />
    </main>
    <PageFooter />
  </div>
</template>

<script>
import PageHeader from "@/components/PageHeader";
import PageFooter from "@/components/PageFooter";
import ChallengeSection from "@/components/FormPage/ChallengeSection/index";
import FormSection from "@/components/FormPage/FormSection/index";

export default {
  name: "FormPage",
  components: {
    FormSection,
    ChallengeSection,
    PageFooter,
    PageHeader,
  },
};
</script>
