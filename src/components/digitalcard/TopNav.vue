<template>
    <div class="d-flex justify-content-around w-100 align-items-center pb-5 mb-2" style="min-height: 300px; background-image: url('/img/pattern.jpg');background-position: center;">
        <div class="row w-100 text-center">
            <div class="col-4 col-md-4 my-3 border-end">
                <div class="fw-bold">
                    <div class="fs-4 d-flex justify-content-center align-items-center">
                        <AutoCounter :data="10" /> +
                    </div>
                    <small>Years Of <br />Experience</small>
                </div>
            </div>
            <div class="col-4 col-md-4 my-3 d-flex align-items-center justify-content-center border-end">
                 <div class="fw-bold">
                    <div class="fs-4 d-flex justify-content-center align-items-center">
                        <AutoCounter :data="150" /> +
                    </div>
                    <small>No. of Happy Customers</small>
                </div>
             </div>
            <div class="col-4 col-md-4 my-3">
                <div class="fw-bold">
                    <div class="fs-4 d-flex justify-content-center align-items-center">
                        <AutoCounter :data="20" /> +
                    </div>
                    <small>Team Members Count</small>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import AutoCounter from '@/components/AutoCounter.vue'
export default {
    name: 'TopNav',
    components: {
        AutoCounter
    },
}
</script>
<style scoped> 
</style>