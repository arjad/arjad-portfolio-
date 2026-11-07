<template>
  <section id="about" class="container">
    <!-- Key Metrics / Achievements Stats -->
    <div class="stats-band">
      <div class="stats-band-bg" style="background-image: url('/office-team.jpg');" aria-hidden="true"></div>
      <div class="container stats-band-content">
        <div class="row justify-content-center">
          <div class="col-6 col-md-3" data-aos="fade-up" data-aos-delay="0">
            <div class="stat-card p-3 text-center">
              <h3 class="stat-number mb-1">7+</h3>
              <p class="stat-label m-0">Years of Experience</p>
            </div>
          </div>
          <div class="col-6 col-md-3" data-aos="fade-up" data-aos-delay="100">
            <div class="stat-card p-3 text-center">
              <h3 class="stat-number mb-1">20+</h3>
              <p class="stat-label m-0">Projects Delivered</p>
            </div>
          </div>
          <div class="col-6 col-md-3" data-aos="fade-up" data-aos-delay="200">
            <div class="stat-card p-3 text-center">
              <h3 class="stat-number mb-1 d-flex align-items-center justify-content-center gap-1">
                5.0 <i class="fa-solid fa-star text-warning fs-2 ms-2 ml-2 "></i>
              </h3>
              <p class="stat-label m-0">Rating</p>
            </div>
          </div>
          <div class="col-6 col-md-3" data-aos="fade-up" data-aos-delay="300">
            <div class="stat-card p-3 text-center">
              <h3 class="stat-number mb-1">15+</h3>
              <p class="stat-label m-0">Clients Worked With</p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="marquee-section mb-5" data-aos="fade">
      <h5 class="text-center text-uppercase text-muted tracking-wider mb-4 fw-bold">Previously Worked With</h5>
      <div class="marquee-container">
        <div class="marquee-track">
          <div 
            v-for="(client, index) in repeatedClients" 
            :key="index" 
            class="company-badge"
          >
            <img :src="client.icon" :alt="client.name" class="company-icon-img" />
            <span class="company-name">{{ client.name }}</span>
          </div>
        </div>
      </div>
    </div>

    <Heading :title="'Industries'" :subtitle="'Delivering bespoke digital solutions, strategic architectures, and product experiences across diverse industry verticals.'" />
    <div class="row g-4 my-5 px-lg-3">
      <div v-for="(industry, index) in industries" :key="index" class="col-12 col-xl-6" data-aos="fade-up" :data-aos-delay="(index % 2) * 120">
        <div class="industry-list-card h-100 p-4 position-relative d-flex flex-column">
          <div class="d-flex align-items-center justify-content-between mb-3 w-100 gap-3">
            <div class="d-flex align-items-center">
              <div class="industry-icon-box flex-shrink-0 d-flex align-items-center justify-content-center" :style="{ backgroundColor: '#f3f4f6' }">
                <i :class="industry.iconClass" style="color: #4b5563; font-size: 1.5rem;"></i>
              </div>
              <h4 class="industry-title fw-bold m-0" style="margin-left: 16px !important;">{{ industry.name }}</h4>
            </div>
            <span class="industry-badge flex-shrink-0" :style="{ backgroundColor: industry.badgeColor, color: industry.badgeTextColor }">
              {{ industry.badgeText }}
            </span>
          </div>
          
          <p class="industry-desc mb-3 flex-grow-1 mt-2">{{ industry.desc }}</p>
          
          <hr class="industry-divider my-2">
          
          <div class="industry-footer d-flex align-items-center mt-auto">
            <div class="industry-tag d-flex align-items-center">
              <span class="tag-dot" :style="{ backgroundColor: industry.tagColor }"></span>
              <span style="margin-left: 8px !important;">{{ industry.tag }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div id="services">
      <Heading :title="'What We Do'" :subtitle="'Complete packages, each starting with a quick discovery call'" />
    </div>

    <div class="what-i-do-grid row justify-content-center my-4">
      <div
        v-for="(service, index) in services"
        :key="service.id"
        class="col-12 col-lg-6 d-flex align-items-stretch my-3"
        data-aos="fade-up"
        :data-aos-delay="(index % 2) * 120"
      >
        <article class="service-card w-100 position-relative d-flex flex-column">
          <div class="d-flex align-items-center">
            <div class="service-icon-wrapper flex-shrink-0">
              <i :class="service.icon + ' service-icon'"></i>
            </div>
            <h4 class="service-title m-0">{{ service.title }}</h4>
          </div>

          <p class="service-desc mt-3 mb-3">{{ service.desc }}</p>

          <p class="included-label">What's included</p>
          <ul class="details-list flex-grow-1">
            <li v-for="(detail, i) in service.details" :key="i" class="detail-item d-flex align-items-center">
              <i class="fa-solid fa-check detail-check flex-shrink-0"></i>
              <span>{{ detail }}</span>
            </li>
          </ul>

          <a :href="discoveryCallLink(service.title)" class="discovery-btn">
            Book a Quick Discovery Call <i class="fa-solid fa-arrow-right"></i>
          </a>
        </article>
      </div>
    </div>
  </section>
</template>

<script>
import Heading from "./common/heading.vue";
export default {
  components: {
    Heading,
  },
  data() {
    return {
      activeSection: 'experience',
      startDate: "2019-01-01",
      discoveryEmail: 'arjadgohar14@gmail.com',
      industries: [
        { 
          name: 'Medical & Healthcare', 
          badgeText: '12+ Projects',
          badgeColor: '#fef2f2',
          badgeTextColor: '#e11d48',
          iconClass: 'fa-regular fa-heart', // outline heart with pulse/plus or similar. fa-heart is good
          iconBg: '#f43f5e',
          desc: 'Telehealth ecosystems, HIPAA-compliant patient portals, EHR workflows, and clinica...',
          tag: 'HealthTech & Compliance',
          tagColor: '#ef4444'
        },
        { 
          name: 'Interior Design', 
          badgeText: '8+ Projects',
          badgeColor: '#fff7ed',
          badgeTextColor: '#c2410c',
          iconClass: 'fa-solid fa-house-user', 
          iconBg: '#f59e0b',
          desc: '3D spatial floor planning, interactive material catalogs, architectural specs, and...',
          tag: '3D & Design Systems',
          tagColor: '#f59e0b'
        },
        { 
          name: 'E-commerce', 
          badgeText: '20+ Platforms',
          badgeColor: '#eff6ff',
          badgeTextColor: '#4338ca',
          iconClass: 'fa-solid fa-bag-shopping', 
          iconBg: '#6366f1',
          desc: 'High-converting headless storefronts, seamless micro-checkouts, omnichannel...',
          tag: 'Headless & Fintech',
          tagColor: '#6366f1'
        },
        { 
          name: 'Real Estate', 
          badgeText: '15+ Portals',
          badgeColor: '#ecfdf5',
          badgeTextColor: '#059669',
          iconClass: 'fa-solid fa-house-chimney', 
          iconBg: '#10b981',
          desc: 'PropTech aggregators, automated tenant portals, MLS API integrations, and 360...',
          tag: 'PropTech & Mapping',
          tagColor: '#10b981'
        }
      ],
      iconClients: [
        { name: 'Lala', icon: '/projects/lala-icon.png' },
        { name: 'Genuity', icon: '/projects/genuity-icon.png' },
        { name: 'Evee', icon: '/projects/evee-icon.jpeg' },
        { name: 'Azoom', icon: '/projects/azoom-icon.png' },
        { name: 'Priwall', icon: '/projects/priwall-icon.png' },
      ],
      services: [
        {
          id: 'website',
          title: 'Website Development',
          icon: 'fa-solid fa-code',
          desc: 'A complete website package, from first design to a stable, secure launch.',
          details: [
            'Custom website design and development',
            'We fix your deployment issues',
            'We fix your security issues',
            'Every integration covered'
          ]
        },
        {
          id: 'application',
          title: 'Application Development',
          icon: 'fa-solid fa-mobile-screen-button',
          desc: 'A complete application package, from your idea to a stable, secure release.',
          details: [
            'Custom application design and development',
            'We fix your deployment issues',
            'We fix your security issues',
            'Every integration covered'
          ]
        },
        {
          id: 'ai-automations',
          title: 'AI Automations',
          icon: 'fa-solid fa-brain',
          desc: 'AI that takes repetitive work off your team and fits into the tools you already use.',
          details: [
            'Custom AI agents and workflow automation',
            'Smart chatbots for your business',
            'We fix your deployment and security issues',
            'Every integration covered'
          ]
        },
        {
          id: 'seo',
          title: 'SEO Services',
          icon: 'fa-solid fa-magnifying-glass-chart',
          desc: 'Driving organic traffic and improving search rankings through data-driven SEO strategies.',
          details: [
            'On-page and technical SEO',
            'Keyword research and strategy',
            'Backlink building and outreach',
            'Performance tracking and analytics'
          ]
        },
        {
          id: 'digital-marketing',
          title: 'Digital Marketing',
          icon: 'fa-solid fa-bullhorn',
          desc: 'Everything your brand needs to get noticed online, handled in one package.',
          details: [
            'Your logo',
            'Your social media handling',
            'Your website development',
            'Your online presence',
            'Your personal branding',
            'SEO',
            'Google AdSense'
          ]
        }
      ]
    };
  },
  computed: {
    calculatedExperience() {
      const startDate = new Date(this.startDate);
      const currentDate = new Date();
      const yearsDifference = currentDate.getFullYear() - startDate.getFullYear();
      const isFullYear = currentDate.getMonth() >= startDate.getMonth() && currentDate.getDate() >= startDate.getDate();

      return isFullYear ? yearsDifference : yearsDifference - 1;
    },
    repeatedClients() {
      return [
        ...this.iconClients, 
        ...this.iconClients, 
        ...this.iconClients, 
        ...this.iconClients
      ];
    }
  },
  methods: {
    setActiveSection(section) {
      this.activeSection = section;
    },
    discoveryCallLink(serviceTitle) {
      const subject = encodeURIComponent(`Quick discovery call: ${serviceTitle}`);
      return `mailto:${this.discoveryEmail}?subject=${subject}`;
    }
  },
};
</script>

<style scoped>
#about {
  margin-top: 40vh;
}

.about-containers {
  gap: 2rem;
}
.details-container {
  padding: 1.5rem;
  flex: 1;
  width: 15vw;
  border-radius: 2rem;
  border: rgb(53, 53, 53) 0.1rem solid;
  border-color: rgb(163, 163, 163);
  text-align: center;
}
.details-container:hover {
  cursor: pointer;
  background: lightgrey;
}

ul {
  line-height: 30px;
  font-size: 1.2rem;
}

.verticle-line{
  width: 15px;
  height: 100%;
  background: linear-gradient(to right, var(--color-primary) 50%, var(--color-secondary) 50%);
}
.verticle-line-right{
  right:0;
}

.text-green{
  color: var(--color-primary);
}
.text-blue{
  color: var(--color-secondary);
  text-decoration: underline;
}

.stats-band {
  width: 100vw;
  position: relative;
  left: 50%;
  right: 50%;
  margin-left: -50vw;
  margin-right: -50vw;
  padding: 10rem 0;
  overflow: hidden;
  isolation: isolate;
}

.stats-band-bg {
  position: absolute;
  top: -16px;
  right: -16px;
  bottom: -16px;
  left: -16px;
  z-index: -2;
  background-size: cover;
  background-position: center 65%;
  filter: blur(4px);
}

.stats-band::after {
  content: '';
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: -1;
  background: rgba(17, 24, 39, 0.62);
}

.stat-card {
  background: rgba(255, 255, 255, 0.12);
  border: 1px solid rgba(255, 255, 255, 0.25);
  border-radius: 18px;
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  transition: transform 0.3s ease, background-color 0.3s ease;
}

.stat-card:hover {
  transform: translateY(-4px);
  background: rgba(255, 255, 255, 0.2);
}

.stat-number {
  font-family: 'Outfit', 'Inter', sans-serif;
  font-size: 2.4rem;
  font-weight: 800;
  font-style: italic;
  color: #ffffff;
  line-height: 1.1;
}

.stat-label {
  font-size: 0.9rem;
  font-weight: 600;
  color: rgba(255, 255, 255, 0.9);
  letter-spacing: 0.01em;
}

.text-warning {
  color: #f59e0b !important;
}

.industry-list-card {
  background: #ffffff;
  border: 1px solid rgba(0, 0, 0, 0.05);
  border-radius: 16px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.03);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  overflow: hidden;

  &::after {
    content: '';
    position: absolute;
    top: -50px;
    right: -20px;
    width: 250px;
    height: 250px;
    background: radial-gradient(circle, rgba(0,0,0,0.02) 0%, transparent 70%);
    border-radius: 50%;
    pointer-events: none;
    z-index: 0;
  }
}

.industry-list-card > * {
  position: relative;
  z-index: 1;
}

.industry-list-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.08);
}

.industry-icon-box {
  width: 52px;
  height: 52px;
  border-radius: 12px;
}

.industry-title {
  color: #111827;
  font-size: 1.4rem;
}

.industry-badge {
  padding: 0.35rem 0.85rem;
  border-radius: 20px;
  font-size: 0.85rem;
  font-weight: 600;
}

.industry-desc {
  color: #6b7280;
  font-size: 1rem;
  line-height: 1.6;
}

.industry-divider {
  border-color: rgba(0, 0, 0, 0.08);
  margin: 1.5rem 0;
}

.industry-tag {
  color: #6b7280;
  font-size: 0.95rem;
  font-weight: 500;
}

.tag-dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  display: inline-block;
}

.marquee-section {
  width: 100vw;
  position: relative;
  left: 50%;
  right: 50%;
  margin-left: -50vw;
  margin-right: -50vw;
  margin-top: 4rem;
  background: rgba(var(--color-secondary-rgb), 0.08);
  border-top: 1px solid rgba(var(--color-secondary-rgb), 0.15);
  border-bottom: 1px solid rgba(var(--color-secondary-rgb), 0.15);
  padding: 2.5rem 0;
  overflow: hidden;
}

.marquee-container {
  width: 100%;
  overflow: hidden;
  position: relative;
  mask-image: linear-gradient(to right, transparent 0%, black 10%, black 90%, transparent 100%);
  -webkit-mask-image: linear-gradient(to right, transparent 0%, black 10%, black 90%, transparent 100%);
}

.marquee-track {
  display: flex;
  gap: 2.5rem;
  width: max-content;
  animation: marqueeScroll 20s linear infinite;

  &:hover {
    animation-play-state: paused;
  }
}

@keyframes marqueeScroll {
  0% { transform: translateX(0); }
  100% { transform: translateX(-33.333%); }
}

.company-icon-img {
  width: 32px;
  height: 32px;
  object-fit: contain;
  border-radius: 0 !important;
}

.company-badge {
  display: inline-flex;
  align-items: center;
  gap: 1.5rem; /* Increased gap to add space between icon and text */
  padding: 0.5rem 1.25rem;
  background: transparent;
  border: none !important;
  border-radius: 0 !important;
  color: #374151;
  font-weight: 600;
  font-size: 1.1rem;
  white-space: nowrap;
  text-decoration: none;
  transition: all 0.3s ease;

  &:hover {
    color: var(--color-primary);
    transform: translateY(-2px);
    background: transparent;
    border: none !important;
    box-shadow: none;
    text-decoration: none;
  }
}

.service-card {
  position: relative;
  overflow: hidden;
  background: rgba(255, 255, 255, 0.6);
  border: 1px solid rgba(0, 0, 0, 0.08);
  border-radius: 20px;
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.04);
  transition: all 0.35s ease;

  &::before {
    content: '';
    position: absolute;
    top: 0;
    left: -150%;
    width: 100%;
    height: 100%;
    background: linear-gradient(
      120deg,
      transparent 0%,
      rgba(255, 255, 255, 0.6) 50%,
      transparent 100%
    );
    transform: skewX(-25deg);
    transition: left 0.75s cubic-bezier(0.4, 0, 0.2, 1);
    pointer-events: none;
    z-index: 5;
  }

  &:hover {
    transform: translateY(-6px);
    border-color: rgba(17, 24, 39, 0.3);
    box-shadow: 0 15px 40px rgba(0, 0, 0, 0.08);

    &::before {
      left: 150%;
    }
  }
}

.service-icon-wrapper {
  width: 52px;
  height: 52px;
  margin-right: 1.25rem;
  border-radius: 14px;
  background: rgba(17, 24, 39, 0.06);
  display: flex;
  align-items: center;
  justify-content: center;
}

.service-icon {
  font-size: 1.5rem;
  color: var(--color-primary);
}

.service-card {
  padding: 2rem;
}

.service-desc {
  font-size: 1rem;
  color: #4b5563;
  line-height: 1.6;
}

.included-label {
  font-size: 0.8rem;
  font-weight: 700;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: #6b7280;
  margin-bottom: 0.75rem;
}

.details-list {
  list-style: none;
  padding: 0;
  margin: 0 0 1.5rem;
}

.detail-item {
  font-size: 0.95rem;
  color: #374151;
  line-height: 1.5;
  font-weight: 500;
  margin-bottom: 0.6rem;
}

.detail-check {
  color: var(--color-primary);
  margin-right: 0.85rem;
}

.discovery-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 0.6rem;
  padding: 0.85rem 1.5rem;
  border-radius: 50px;
  background: var(--color-primary);
  color: #ffffff;
  font-weight: 700;
  text-decoration: none;
  transition: background-color 0.3s ease, transform 0.3s ease;
}

.discovery-btn:hover {
  background: var(--color-secondary);
  color: #ffffff;
  text-decoration: none;
  transform: translateY(-2px);
}

.service-title {
  font-size: 1.25rem;
  font-weight: 700;
  color: #111827;
}

@media screen and (max-width: 991.98px) {
  #about {
    margin-top: 100px;
  }

  .service-icon-wrapper {
    width: 44px !important;
    height: 44px !important;
    border-radius: 12px !important;
  }

  .service-icon {
    font-size: 1.2rem !important;
  }

  .service-title {
    font-size: 1.15rem !important;
  }

  .service-card {
    padding: 1.5rem;
  }

  .stats-band {
    padding: 6rem 0;
  }

  .stats-band .col-6 {
    padding: 0.5rem;
  }

  .stat-number {
    font-size: 1.65rem !important;
  }

  .stat-label {
    font-size: 0.78rem !important;
  }

  .stat-card {
    padding: 0.85rem 0.5rem !important;
    border-radius: 14px !important;
  }
}

@media screen and (max-width: 375px) {
  .details-container h3 {
    font-size: 14px;
  }
}
</style>
