<template>
    <div class="bg-light">
        <div class="">
            <ServicesFormBanner />
        </div>
        <div class="">
            <BusinessCard />
        </div>
    </div>
</template>
<script>
import ServicesFormBanner from "@/components/business-site/services/FormBanner.vue";
import BusinessCard from "@/components/business-site/BusinessCard.vue";
export default {
    name:"BusinessPage",
    components:{
        ServicesFormBanner,
        BusinessCard,
    }
}
</script>
<style lang="">

</style>