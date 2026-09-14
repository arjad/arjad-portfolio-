<template>
  <div class="essora">
    <Summary id="summary" />
    <About id="about" />
    <!-- Skills section removed as requested for /essora -->
    <Project id="projects" :limit="4" />
    <div class="container text-center mt-4 mb-5 pb-5">
      <router-link to="/projects" class="btn btn-custom-green px-4 rounded-pill shadow-sm">
        View All Projects <i class="fa-solid fa-arrow-right ms-2"></i>
      </router-link>
    </div>
    <Journey id="journey" />
    <SocialStats id="social_stats" />
    <WriteMe id="write_me" />
    <Contact id="contact" />
  </div>
</template>

<script>
import Summary from "../components/summary.vue";
import About from "../components/about.vue";
import Project from "../components/project.vue";
import Journey from "../components/journey.vue";
import Contact from "../components/contact.vue";
import WriteMe from "../components/writeMe.vue";
import SocialStats from "../components/socialStats.vue";

export default {
  name: "Essora",
  components: {
    Summary,
    About,
    Project,
    Journey,
    Contact,
    WriteMe,
    SocialStats,
  },
};
</script>

<style scoped>
.btn-custom-green {
  color: #42b883;
  border: 1px solid #42b883;
  background-color: transparent;
  transition: all 0.3s ease;
}
.btn-custom-green:hover {
  background-color: #42b883;
  color: white;
}
</style>
