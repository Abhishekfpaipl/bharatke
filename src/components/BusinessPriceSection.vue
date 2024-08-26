<template>
    <div class="my-3 py-3">
        <div class="d-md-flex justify-content-center gap-3">
            <div v-for="(plan, index) in plans" :key="index" class="card mb-3 px-3 py-2 text-white rounded-0"
                style="background-color:black !important;" :class="{ 'recommended': index === 1 }">

                <div v-if="index === 1" class="position-absolute start-0 m-2 ms-0" style="font-size: 12px; top: 5px;">
                    <span class='text-dark fw-bold bg-warning p-1 px-2 rounded-end-3'>Recommended</span>
                </div>

                <div class="py-2 border-bottom fw-bold">{{
                    plan.name }}</div>
                <div class="card-body text-center">
                    <div class="d-flex justify-content-center align-items-center gap-2">
                        <p class=" mb-0">Starting from</p>
                        <p v-if="plan.price" class="mb-0 card-title fs-3">₹ <span class="fw-bold">{{
                            plan.price }} </span></p>
                        <p v-else class="mb-0 card-title fs-3 fw-bold">Custom</p>
                    </div>
                    <p v-if="plan.price"><small class="text-capitalize">{{ plan.tag
                            }}</small></p>
                    <p v-else>Price, as per requirement</p>
                    <div v-if="plan.price" class="d-flex justify-content-center align-items-center">
                        <p class="fw-light d-inline-block px-4 rounded-3" style="background-color: var(--brand-color)">
                            <span class="text-decoration-line-through text-danger fw-bold">{{ plan.mrp }}</span>
                            <span class="text-danger fw-bold"> ({{ getDiscount(plan) }}% discount)</span>
                        </p>
                    </div>
                    <p v-else class="fw-bold d-inline-block px-4 rounded-3 text-danger"
                        style="background-color: var(--brand-color)"> No discount available</p>

                    <ul v-if="plan.features" class="list-group">
                        <small class="text-start text-uppercase fw-bold my-2 "
                            style="color:var(--brand-color) !important;">{{ plan.key
                            }}</small>
                        <li v-for="(feature, featureIndex) in plan.features.slice(0, 4)" :key="featureIndex"
                            class="px-0 d-flex text-white justify-content-between list-group-item text-start text-capitalize border-0"
                            style="background-color:black !important;">
                            <div class="">
                                <i class="bi bi-check-circle" style="color:var(--brand-color) !important;"></i>
                                <span class="px-2">
                                    {{ feature.text }}
                                </span>
                            </div>
                            <i class="bi bi-info-circle" data-bs-toggle="tooltip" data-bs-placement="top"
                                data-bs-custom-class="custom-tooltip" :data-bs-title="feature.tooltip"></i>
                        </li>
                    </ul>
                </div>
                <div class="card-footer  p-0 border-top pt-2">
                    <p class="card-text text-capitalize">{{ plan.description }}</p>

                    <div class="btn-group w-100 my-2">
                        <a :href="'https://wa.me/8860012001?text=' + encodeURIComponent('Hello, I want to get your ' + ' service')"
                            class="btn text-capitalize px-4 text-dark btn-warning">
                            <i class="bi bi-whatsapp"></i>
                            <span class="ms-2">Enquiry</span>
                        </a>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "PriceSection",
    data() {
        return {
            plans: [
                {
                    id: 1,
                    name: "Starter",
                    price: "500",
                    mrp: "5,000",
                    link: "/digital-marketing/",
                    tag: "/user/yearly/billed yearly",
                    description: "Start with our Starter plan and upgrade only when you need additional features.",
                    button: "Get Started",
                    key: "key features",
                    features: [
                        {
                            text: "Search Engine Optimization (SEO)",
                            tooltip: "Improve rankings with on-page and off-page SEO techniques."
                        },
                        {
                            text: "Pay-Per-Click Advertising (PPC)",
                            tooltip: "Manage paid ads on search engines and social media for targeted visibility."
                        },
                        {
                            text: "Content Marketing",
                            tooltip: "Create and distribute engaging content to attract and retain audiences."
                        },
                        {
                            text: "Social Media Marketing (SMM)",
                            tooltip: "Manage social media content and run targeted ad campaigns."
                        },
                        {
                            text: "Email Marketing",
                            tooltip: "Design and execute personalized email campaigns for better engagement."
                        },
                        {
                            text: "Influencer Marketing",
                            tooltip: "Partner with influencers to endorse products and reach new audiences."
                        },
                        {
                            text: "Conversion Rate Optimization (CRO)",
                            tooltip: "Optimize websites to increase conversion rates through data analysis."
                        },
                        {
                            text: "Analytics and Reporting",
                            tooltip: "Monitor and analyze marketing metrics to inform strategic decisions."
                        },
                        {
                            text: "Online Reputation Management (ORM)",
                            tooltip: "Manage online reviews and feedback to maintain a positive brand image."
                        },
                        {
                            text: "Mobile Marketing",
                            tooltip: "Optimize marketing strategies for mobile users and mobile-specific behaviors."
                        },
                        {
                            text: "Customer Relationship Management (CRM)",
                            tooltip: "Use CRM systems to manage leads and personalize marketing efforts."
                        },
                        {
                            text: "Marketing Automation",
                            tooltip: "Automate marketing tasks with tools like HubSpot, Marketo, or Mailchimp."
                        },
                    ]
                },
                {
                    id: 2,
                    name: "Enterprise",
                    price: "1000",
                    mrp: "10,000",
                    link: "/digital-marketing/",
                    tag: "/user/yearly/billed yearly",
                    description: "Choose the right set of features you need to begin your  journey.",
                    button: "Get Started",
                    button2: "Buy now",
                    key: "key features",
                    features: [
                        {
                            text: "Search Engine Optimization (SEO)",
                            tooltip: "Improve rankings with on-page and off-page SEO techniques."
                        },
                        {
                            text: "Pay-Per-Click Advertising (PPC)",
                            tooltip: "Manage paid ads on search engines and social media for targeted visibility."
                        },
                        {
                            text: "Content Marketing",
                            tooltip: "Create and distribute engaging content to attract and retain audiences."
                        },
                        {
                            text: "Social Media Marketing (SMM)",
                            tooltip: "Manage social media content and run targeted ad campaigns."
                        },
                        {
                            text: "Email Marketing",
                            tooltip: "Design and execute personalized email campaigns for better engagement."
                        },
                        {
                            text: "Influencer Marketing",
                            tooltip: "Partner with influencers to endorse products and reach new audiences."
                        },
                        {
                            text: "Conversion Rate Optimization (CRO)",
                            tooltip: "Optimize websites to increase conversion rates through data analysis."
                        },
                        {
                            text: "Analytics and Reporting",
                            tooltip: "Monitor and analyze marketing metrics to inform strategic decisions."
                        },
                        {
                            text: "Online Reputation Management (ORM)",
                            tooltip: "Manage online reviews and feedback to maintain a positive brand image."
                        },
                        {
                            text: "Mobile Marketing",
                            tooltip: "Optimize marketing strategies for mobile users and mobile-specific behaviors."
                        },
                        {
                            text: "Customer Relationship Management (CRM)",
                            tooltip: "Use CRM systems to manage leads and personalize marketing efforts."
                        },
                        {
                            text: "Marketing Automation",
                            tooltip: "Automate marketing tasks with tools like HubSpot, Marketo, or Mailchimp."
                        },
                    ]
                },
                {
                    id: 3,
                    name: "Business",
                    // price: "5,000",
                    // mrp: "50,000",
                    link: "/digital-marketing/",
                    tag: "/user/yearly/billed yearly",
                    description: "Enjoy our advanced offering for fast-growing businesses and startups.",
                    button: "Get Started",
                    button2: "Buy now",
                    key: "key features",
                    features: [
                        {
                            text: "Search Engine Optimization (SEO)",
                            tooltip: "Improve rankings with on-page and off-page SEO techniques."
                        },
                        {
                            text: "Pay-Per-Click Advertising (PPC)",
                            tooltip: "Manage paid ads on search engines and social media for targeted visibility."
                        },
                        {
                            text: "Content Marketing",
                            tooltip: "Create and distribute engaging content to attract and retain audiences."
                        },
                        {
                            text: "Social Media Marketing (SMM)",
                            tooltip: "Manage social media content and run targeted ad campaigns."
                        },
                        {
                            text: "Email Marketing",
                            tooltip: "Design and execute personalized email campaigns for better engagement."
                        },
                        {
                            text: "Influencer Marketing",
                            tooltip: "Partner with influencers to endorse products and reach new audiences."
                        },
                        {
                            text: "Conversion Rate Optimization (CRO)",
                            tooltip: "Optimize websites to increase conversion rates through data analysis."
                        },
                        {
                            text: "Analytics and Reporting",
                            tooltip: "Monitor and analyze marketing metrics to inform strategic decisions."
                        },
                        {
                            text: "Online Reputation Management (ORM)",
                            tooltip: "Manage online reviews and feedback to maintain a positive brand image."
                        },
                        {
                            text: "Mobile Marketing",
                            tooltip: "Optimize marketing strategies for mobile users and mobile-specific behaviors."
                        },
                        {
                            text: "Customer Relationship Management (CRM)",
                            tooltip: "Use CRM systems to manage leads and personalize marketing efforts."
                        },
                        {
                            text: "Marketing Automation",
                            tooltip: "Automate marketing tasks with tools like HubSpot, Marketo, or Mailchimp."
                        },
                    ]
                }
            ]
        }
    },
    mounted() {
        this.initTooltips();
    },
    updated() {
        this.initTooltips();
    },
    methods: {
        initTooltips() {
            // Initialize tooltips (assuming using Bootstrap's tooltip)
            const tooltipTriggerList = [].slice.call(
                document.querySelectorAll('[data-bs-toggle="tooltip"]')
            );
            tooltipTriggerList.forEach(function (tooltipTriggerEl) {
                new window.bootstrap.Tooltip(tooltipTriggerEl);
            });
        },
        getDiscount(plan) {
            if (plan.mrp && typeof plan.mrp === 'string') {
                const mrp = parseFloat(plan.mrp.replace(/[^\d.-]/g, ''));
                const price = parseFloat(plan.price.replace(/[^\d.-]/g, ''));
                if (!isNaN(mrp) && !isNaN(price) && mrp > 0) {
                    return ((mrp - price) / mrp * 100).toFixed(0);
                }
            }
            return 0; // Default return if calculation fails
        }

    }
};
</script>
