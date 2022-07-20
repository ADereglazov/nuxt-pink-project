<template>
  <div>
    <PageHeader />
    <main class="page-main">
      <h1 class="visually-hidden">Отзывы пользователей Pink</h1>
      <PhotosSection />
      <GallerySection />
      <PhotoEditorSection />
    </main>
    <PageFooter />
  </div>
</template>

<script>
import PageHeader from "@/components/PageHeader";
import PageFooter from "@/components/PageFooter";
import PhotosSection from "@/components/PhotoPage/PhotosSection/index";
import GallerySection from "@/components/PhotoPage/GallerySection/index";
import PhotoEditorSection from "@/components/PhotoPage/PhotoEditorSection/index";

export default {
  name: "PhotoPage",
  components: {
    PhotoEditorSection,
    GallerySection,
    PhotosSection,
    PageFooter,
    PageHeader,
  },
};
</script>
