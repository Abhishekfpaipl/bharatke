<template>
    <div class="container my-5">
        <h1 class="mb-2">
            <span class="text-warning">Your Journey</span> on Bharatke
        </h1>
        <p class="text-muted mb-4">
            Starting your online business with Bharatke is easy. 14 lakh+ sellers trust Bharatke with their business
        </p>

        <div class="row row-cols-1 row-cols-md-3 row-cols-lg-4 g-2">
            <div class="col mb-4" v-for="(step, index) in steps" :key="index">
                <div class="card h-100 border-0 bg-light">
                    <div class="card-body text-center">
                        <img :src="step.image" :alt="step.title" class="img-fluid mb-3" style="height: 100px;">
                        <h5 class="card-title">{{ step.title }}</h5>
                        <p class="card-text small">{{ step.description }}</p>
                    </div>
                </div>
            </div>
        </div>

        <div class="text-center mt-4">
            <button class="btn btn-warning">Download Launch Kit</button>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            steps: [
                {
                    title: "Create",
                    description: "Register in just 10 mins with valid GST, address, & bank details",
                    image: "https://static-assets-web.flixcart.com/fk-sp-static/images/create-icon.svg"
                },
                {
                    title: "List",
                    description: "List your products (min 1 no.) that you want to sell on Bharatke.",
                    image: "https://static-assets-web.flixcart.com/fk-sp-static/images/prelogin/icons/Group_2_1.svg"
                },
                {
                    title: "Orders",
                    description: "Receive orders from over 45 crore+ Bharatke customers.",
                    image: "https://static-assets-web.flixcart.com/fk-sp-static/images/orders-icon.svg"
                },
                {
                    title: "Shipment",
                    description: "Bharatke ensures stress free delivery of your products",
                    image: "https://static-assets-web.flixcart.com/fk-sp-static/images/shipment-icon.svg"
                },
                {
                    title: "Payment",
                    description: "Receive payment 7 days* from the date of dispatch of your order",
                    image: "https://static-assets-web.flixcart.com/fk-sp-static/images/payment-icon.svg"
                }
            ]
        };
    }
};
</script>

<style scoped>
.card {
    transition: transform 0.3s ease-in-out;
}

.card:hover {
    transform: translateY(-5px);
}
</style>