<template>
  <div class="container pb-3">
    <h1 class="text-center mb-5">Courses & Education</h1>
    <div class="position-relative my-5">
      <div class="d-flex gap-3 overflow-x-scroll" id="scroll" ref="scrollContainer">
        <div class="" v-for="(course, index) in courses" :key="index">
          <div class="card" style="min-width: 18rem; min-height: 12rem">
            <div class="card-body p-0">
              <h5 class="text-center card-title border-bottom py-3 bg-light" style="min-height: 81px;">{{ course.title }}</h5>
              <p class="card-text px-2 overflow-scroll text-ellipsis4" id="scroll">{{ course.description }}</p>
            </div>
          </div>
        </div>
      </div>
      <div class="rounded-circle border d-flex justify-content-center align-items-center position-absolute bg-light"
        @click="scrollLeft" style="width: 40px; height:40px ;top: 40%; left: -2%">
        <i class="bi bi-chevron-left"></i>
      </div>
      <div class="rounded-circle border d-flex justify-content-center align-items-center position-absolute bg-light"
        @click="scrollRight" style="width: 40px; height:40px ;top: 40%; right: -2%">
        <i class="bi bi-chevron-right"></i>
      </div>
    </div>

    <div class="my-5">
      <h1 class="text-center mb-5">Skillset</h1>
      <div class="row row-cols-1 row-cols-md-2 g-md-5 g-2">
        <div class="col mt-2" v-for="(skill, index) in skills" :key="index">
          <h5 class="mb-1 mt-3 text-uppercase">{{ skill.skill }} </h5>
          <div class="progress rounded-0" role="progressbar" aria-label="Danger example" aria-valuenow="100"
            aria-valuemin="0" aria-valuemax="100">
            <div class="progress-bar-striped" :class="skill.bg" :style="{ width: skill.percent + '%' }"> {{
              skill.percent
            }}
              %</div>
          </div>
        </div>
      </div>
    </div>


    <div class="row m-2 my-5" v-for="(edu, index) in education " :key="index">
      <div class="col-12">
        <div class="border p-2 bg-light">
          <h1 class="text-center mb-2">{{ edu.year }}</h1>
          <p class="mb-1 text-center fw-bold fs-4 ">{{ edu.post }}</p>
          <p class="mb-1 text-center">{{ edu.company }}</p>
        </div>
      </div>
      <div class="col-12">
        <ol class="list-group list-group-numbered rounded-0">
          <li class="list-group-item text-start" v-for="(point, pointIndex) in edu.points" :key="pointIndex">{{ point }}
          </li>
        </ol>
      </div>
    </div>
  </div>
  <CustomCounter service="satisfied customers" :serviceCount="1000" category="years of expirence" :categoryCount="10"
    place="projects completed" :placeCount="4000" title="fun facts" />
  <ContactSection />
</template>

<script>
import ContactSection from "@/components/ContactSection.vue"
import CustomCounter from "@/components/CustomCounter.vue"
export default {
  name: 'AboutusSection',
  components: {
    ContactSection,
    CustomCounter,
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
  methods: {
    scrollLeft() {
      const container = this.$refs.scrollContainer;
      const scrollWidth = container.clientWidth;
      const newScrollLeft = Math.max(container.scrollLeft - scrollWidth);

      container.scrollTo({
        left: newScrollLeft,
        behavior: 'smooth'
      });
    },
    scrollRight() {
      const container = this.$refs.scrollContainer;
      const scrollWidth = container.clientWidth;
      const maxScrollLeft = container.scrollWidth - scrollWidth;
      const newScrollLeft = Math.min(container.scrollLeft + scrollWidth, maxScrollLeft);

      container.scrollTo({
        left: newScrollLeft,
        behavior: 'smooth'
      });
    }
  }
}
</script>

<style scoped>
.card-text {
  max-height: 12rem;
  /* Adjust as needed */
  overflow-y: auto;
}

#scroll::-webkit-scrollbar {
  display: none;
}
</style>
