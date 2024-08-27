<template>
    <div class=" ">
      <div class="">
        <BannerSection />
      </div> 
      
    </div>
  </template>
  
  <script>
  import BannerSection from "@/components/BannerSection.vue"; 
  export default {
    name: "HomeView",
    components: {
      BannerSection, 
    },
  };
  </script>