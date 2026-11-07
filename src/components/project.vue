<template>
  <section id="projects">
    <Heading v-if="showHeading" :title="'Our Projects'" :subtitle="'Have a look at'" />

    <section class="project-container container-fluid">
      <div v-for="(project, index) in displayedProjects" :key="index" class="project-item" data-aos="fade-up" :data-aos-delay="(index % 3) * 120">
      <div class="card px-0 h-100" @click="goToProject(project.id)" style="cursor: pointer;">
        <img :src="project.image" class="card-img-top" :alt="project.title"/>

        <div class="card-body shadow">
            <h5 class="card-title">{{ project.title }}</h5>
            <p class="card-text">{{ project.description }}</p>
            <div class="d-flex flex-wrap mt-2">
                <a :href="project.github" target="_blank" class="btn me-2 mb-2" @click.stop>
                  <i class="fa-brands fa-github mr-2"></i>Code
                </a>
                <a :href="project.live" target="_blank" class="btn me-2 mb-2" @click.stop>
                  <i class="fa-solid fa-arrow-up-right-from-square mr-1"></i> View
                </a>
            </div>
        </div>
      </div>
      </div>
    </section>
  </section>
</template>

<script>
  import VueSlickCarousel from 'vue-slick-carousel'
  import 'vue-slick-carousel/dist/vue-slick-carousel.css'
  import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'
  import Heading from "./common/heading.vue";
  import projectsData from "../data/projects.json";
 
  export default {
    name: 'MyComponent',
    components: { VueSlickCarousel, Heading },
    props: {
      limit: {
        type: Number,
        default: 0
      },
      categoryFilter: {
        type: String,
        default: 'All'
      },
      showHeading: {
        type: Boolean,
        default: true
      }
    },
    methods: {
      viewUrl(url) {
        window.location.href = url;
      },
      goToProject(id) {
        this.$router.push(`/project/${id}`);
      }
    },
    data() {
      return {
        projects: projectsData
      };
    },
    computed: {
      displayedProjects() {
        let filtered = this.projects;
        if (this.categoryFilter && this.categoryFilter !== 'All') {
          filtered = filtered.filter(p => 
            p.category === this.categoryFilter || 
            (p.technologies && p.technologies.some(t => t.toLowerCase() === this.categoryFilter.toLowerCase()))
          );
        }
        if (this.limit > 0) {
          return filtered.slice(0, this.limit);
        }
        return filtered;
      }
    }
  }
</script>

<style scoped lang="scss">
.project-container {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 24px;
  max-width: 1040px;
  @media screen and (max-width: 991.98px) {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }
  @media screen and (max-width: 600px) {
    grid-template-columns: minmax(0, 1fr);
  }
  .card-img-top {
    height: 11rem;
    object-fit: cover;
    object-position: top;
  }
  .card {
    transition: transform 0.3s ease-in-out;
    background: transparent;

    &:hover{
      transform: scale(1.02);
      z-index:2;
    }
  }
}

</style>