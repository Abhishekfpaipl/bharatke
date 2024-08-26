<template>
    <div class="min-vh-100 d-flex justify-content-center align-items-center"
        style="background: linear-gradient(90deg, rgba(254,242,159,1) 0%, rgba(210,163,73,1) 50%, rgba(254,242,159,1) 100%);">
        <div class="container w-100 pt-5">
            <div class="d-md-flex d-none justify-content-evenly align-items-center w-100 mb-5">
                <div class="d-flex align-items-center">
                    <TextStyle />
                </div>
            </div>
            <div class="d-md-none d-flex flex-column justify-content-center align-items-center w-100 mb-5">
                <div class="d-flex align-items-center" style="font-size: 20px !important;">
                    <TextStyle />
                </div>
            </div>
            <RouterLink to="/review-list" class="mt-4 text-decoration-none w-100 rounded">
                <div class="my-1 rounded-0 btn btn-light border py-2 w-100 d-flex justify-content-between">
                    <div class='d-flex'>
                        <span class="fw-bold">Search by</span> &nbsp;
                        <span class="text-secondary">{{ searchText }}</span>
                    </div>
                    <i class="bi bi-search"></i>
                </div>
            </RouterLink>
            <div class="flex-fill  w-100 d-flex flex-column justify-content-center">
                <div class="w-100 pb-5 mt-4">
                    <div class="container d-md-flex d-block justify-content-between align-items-center">
                    </div>
                </div>
            </div>
            <!-- <div class="d-flex justify-content-center align-items-center gap-4">
                <router-link to="/registration-page"
                    class="d-flex flex-column align-items-center justify-content-center btn btn-danger rounded">
                    <i class="bi bi-person-plus"></i>
                    <span>Register</span>
                </router-link>
                <router-link to="/story"
                    class="d-flex flex-column align-items-center justify-content-center btn btn-danger rounded">
                    <i class=" bi bi-shop"></i>
                    <span>Shop</span>
                </router-link>
                <router-link to="/dashboard"
                    class="d-flex flex-column align-items-center justify-content-center btn btn-danger rounded">
                    <i class="bi bi-person-circle "></i>
                    <span>Login</span>
                </router-link>
                <router-link to="/digital-card"
                    class="d-flex flex-column align-items-center justify-content-center btn btn-danger rounded">
                    <i class="bi bi-person "></i>
                    <span>Profile</span>
                </router-link>
            </div> -->
            <div class="d-flex justify-content-center align-items-center gap-4 mt-5">
                <router-link to="/digital-card"
                    class="d-flex flex-column align-items-center justify-content-center btn btn-danger rounded">
                    <i class="bi bi-person-plus"></i>
                    <span>Digital Card</span>
                </router-link>
                <!-- <router-link to="/digital-card-professional"
                    class="d-flex flex-column align-items-center justify-content-center btn btn-danger rounded">
                    <i class=" bi bi-shop"></i>
                    <span>Professionals</span>
                </router-link>
                <router-link to="/digital-card-service"
                    class="d-flex flex-column align-items-center justify-content-center btn btn-danger rounded">
                    <i class="bi bi-person-circle "></i>
                    <span>Service Provider</span>
                </router-link>
                <router-link to="/digital-card"
                    class="d-flex flex-column align-items-center justify-content-center btn btn-danger rounded">
                    <i class="bi bi-person "></i>
                    <span>Retailer</span>
                </router-link>
                <router-link to="/digital-card-student"
                    class="d-flex flex-column align-items-center justify-content-center btn btn-danger rounded">
                    <i class="bi bi-person "></i>
                    <span>Student</span>
                </router-link> -->
            </div>
        </div>
    </div>
</template>
<script>
import TextStyle from "@/components/TextStyle.vue";
export default {
    components: {
        TextStyle
    },
    data() {
        return {
            searchText: '',
            currentIndex: 0,
            words: ['City', 'Clothing', 'Categories', 'Top Retailer'],
        }
    },
    mounted() {
        this.rotateWords();
    },
    methods: {
        rotateWords() {
            setTimeout(() => {
                this.searchText = this.words[this.currentIndex];
                this.currentIndex++;
                if (this.currentIndex >= this.words.length) {
                    this.currentIndex = 0;
                }
                this.rotateWords();
            }, 1000);
        },
    }

}
</script>
<style lang="">

</style>