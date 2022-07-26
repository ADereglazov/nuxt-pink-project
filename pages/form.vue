<template>
  <div>
    <PageHeader />
    <main class="page-main" @keydown.esc="handleKeyDown">
      <h1 class="visually-hidden">Конкурс от Pink</h1>
      <ChallengeSection />
      <FormSection
        :is-focus="isModalFailureOpen"
        @form-failure="isModalFailureOpen = true"
        @form-sent="isModalSentOpen = true"
      />
      <ModalFailure
        v-show="isModalFailureOpen"
        :open="isModalFailureOpen"
        @close-modal-failure="isModalFailureOpen = false"
      />
      <ModalSent
        v-show="isModalSentOpen"
        :open="isModalSentOpen"
        @close-modal-sent="isModalSentOpen = false"
      />
    </main>
    <PageFooter />
  </div>
</template>

<script>
import PageHeader from "@/components/PageHeader";
import PageFooter from "@/components/PageFooter";
import ChallengeSection from "@/components/FormPage/ChallengeSection";
import FormSection from "@/components/FormPage/FormSection";
import ModalFailure from "@/components/FormPage/ModalFailure";
import ModalSent from "@/components/FormPage/ModalSent";

export default {
  name: "FormPage",
  components: {
    ModalSent,
    ModalFailure,
    FormSection,
    ChallengeSection,
    PageFooter,
    PageHeader,
  },
  data: () => ({
    isModalFailureOpen: false,
    isModalSentOpen: false,
  }),
  methods: {
    handleKeyDown() {
      this.isModalFailureOpen = false;
      this.isModalSentOpen = false;
    },
  },
};
</script>
