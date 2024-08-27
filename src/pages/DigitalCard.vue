<template>
  <div class=" ">
    <DigitalTop :user="user" />
    <TopNav />
    <TopSection :user="user" />
    <ContactCard :user="user"/>
    <InfoSection :user="user"/>
    <SocialSchedule />
    <DigitalFooter />
    <CollectionSection />


  </div>
</template>

<script>

import TopNav from '@/components/digitalcard/TopNav.vue'
import TopSection from '@/components/digitalcard/TopSection.vue'
// import CollectionSection from '@/components/digitalcard/CollectionSection.vue'
import InfoSection from '@/components/digitalcard/InfoSection.vue';
import SocialSchedule from '@/components/digitalcard/SocialSchedule.vue';
import ContactCard from '@/components/digitalcard/ContactCard.vue';
import DigitalFooter from '@/components/digitalcard/DigitalFooter.vue';
import DigitalTop from '@/components/digitalcard/DigitalTop.vue';

export default {
  name: "DigitalCard",
  components: {
    TopSection,
    TopNav,
    // CollectionSection,
    InfoSection,
    ContactCard,
    SocialSchedule,
    DigitalFooter,
    DigitalTop
  },
  data() {
    return {
      userId: '',
      name: '',
      email: '',
      query: ''
    }
  },
  computed: {
    user() {
      let userId = this.$route.params.userMobile;
      return this.$store.getters.getUser(userId);
    },
  },
  methods: {
    submitQuery() {
      console.log('Submit Query')
      const data = {
        name: this.name,
        email: this.email,
        query: this.query,
      }
      this.$store.dispatch('submitQuery', data)
    },
  }

};
</script>
<style>
.query {
  z-index: 9;
  position: fixed;
  bottom: 60px;
  right: 10px;
  padding: 10px 10px;
  cursor: pointer;
  border-radius: 5px;
  display: flex;
  align-items: center;
}
</style>