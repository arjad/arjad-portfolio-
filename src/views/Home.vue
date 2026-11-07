<template>
  <div class="home">
    <Summary id="summary" />
    <About id="about" />
    <Process />
    <Project id="projects" :limit="3" />
    <div class="container text-center mt-5 mb-5 pb-5" data-aos="fade-up">
      <router-link to="/projects" class="btn btn-custom-green px-4 rounded-pill shadow-sm">
        View All Projects <i class="fa-solid fa-arrow-right ms-2"></i>
      </router-link>
    </div>
    <SocialStats id="social_stats" />
        <WriteMe id="write_me" />

    <Contact id="contact" />
  </div>
</template>

<script>
import Summary from "../components/summary.vue";
import About from "../components/about.vue";
import Process from "../components/process.vue";
import Project from "../components/project.vue";
import Contact from "../components/contact.vue";
import WriteMe from "../components/writeMe.vue";
import SocialStats from "../components/socialStats.vue";

export default {
  name: "Home",
  components: {
    Summary,
    About,
    Process,
    Project,
    Contact,
    WriteMe,
    SocialStats,
  },
};
</script>

<style scoped>
.btn-custom-green {
  color: white;
  border: 1px solid var(--color-primary);
  background-color: var(--color-primary);
  transition: all 0.3s ease;
}
.btn-custom-green:hover {
  background-color: var(--color-secondary);
  border-color: var(--color-secondary);
  color: white;
}
</style>
