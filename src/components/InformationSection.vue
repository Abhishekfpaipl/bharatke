<template>
    <div>
        <ul class="px-2 nav nav-pills justify-content-start align-items-center sticky-nav" id="pills-tab"
            role="tablist">
            <div class="d-flex overflow-x-scroll gap-1 p-2 pe-3 px-0 rounded" id="scroll">
                <li class="nav-item border rounded" role="presentation" v-for="(collection, index) in tabs"
                    :key="index">
                    <div class="d-md-flex justify-content-center align-items-center gap-2 nav-link p-2 text-dark"
                        style="background-color:rgba(255, 206, 86, 0.2); border:1px solid rgba(255, 206, 86, 1) !important;white-space:nowrap;"
                        :class="{ 'active': index === activeTabIndex }" :id="'tab-' + index" data-bs-toggle="pill"
                        :data-bs-target="'#content-' + index" role="tab" :aria-controls="'#content-' + index"
                        :aria-selected="index === activeTabIndex" @click="onTabClick(index)">
                        <p class="mb-0">{{ collection.name }}</p>
                        <p class="mb-0">{{ collection.count }} + </p>
                    </div>
                </li>
            </div>
        </ul>
        <div class="tab-content mt-3" id="pills-tabContent">
            <div class="tab-pane fade" :class="{ 'show active': index === activeTabIndex }"
                v-for="(collection, index) in tabs" :key="index" :id="'content-' + index" role="tabpanel"
                :aria-labelledby="'tab-' + index" tabindex="0">
                <component :is="collection.component" :skills="skills" :education="education" :courses="courses" />
            </div>
        </div>
    </div>

</template>

<script>
import TimelineSection from '@/components/TimelineSection.vue';
import AboutusSection from "@/components/AboutusSection.vue";
import AchievementsSection from "@/components/AchievementsSection.vue";
import ReviewSection from "@/components/ReviewSection.vue";
import PromotionSection from '@/components/PromotionSection.vue';
export default {
    name: "InformationSection",
    components: {
        AboutusSection,
        AchievementsSection,
        TimelineSection,
        ReviewSection,
        PromotionSection,
    },
    props: {
        skills: {
            type: Array,
            required: true,
        },
        education: {
            type: Array,
            required: true,
        },
        courses: {
            type: Array,
            required: true,
        }
    },
    data() {
        return {
            tabs: [
                { count: "10", id: 'Showcase', name: 'Showcase', component: 'AchievementsSection' },
                { count: "20", id: 'Review', name: 'Review', component: 'ReviewSection' },
                { count: "30", id: 'Timeline', name: 'Timeline', component: 'TimelineSection' },
                { count: "50", id: 'Promoters', name: 'Promoters', component: 'PromotionSection' },
                { count: "50", id: 'About', name: 'About', component: 'AboutusSection' },
            ],
            activeTabIndex: 0,
           
        }
    },

    methods: {
        onTabClick(index) {
            this.activeTabIndex = index;
            this.scrollTabIntoView(index);
        },
        scrollTabIntoView(index) {
            const tabElement = document.getElementById(`tab-${index}`);
            if (tabElement) {
                tabElement.scrollIntoView({ behavior: 'smooth', inline: 'center', block: 'nearest' });
            }
        }
    }
}
</script>
<style scoped>
.nav-link.active {
    background-color: black !important;
    color: #FFF5DD !important;
    border-bottom: 2px solid red !important;
}



.sticky-nav {
    /* position: -webkit-sticky; */
    /* For Safari */
    position: sticky;
    top: 0px !important;
    z-index: 1000;
    background-color: white;
}
</style>