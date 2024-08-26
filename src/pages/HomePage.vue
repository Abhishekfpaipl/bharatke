<template>
  <div class="home">
    <div class="">
      <BannerSection />
    </div>
    <div class="">
      <TestComponent />
    </div>
    
  </div>
</template>

<script>
import BannerSection from "@/components/BannerSection.vue";
// import TestComponent from "@/components/TestComponent.vue";
export default {
  name: "HomeView",
  components: {
    BannerSection,
    // TestComponent,
  },
};
</script>
