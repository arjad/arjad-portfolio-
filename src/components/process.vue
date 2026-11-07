<template>
  <section id="process" class="process-section">
    <Heading :title="'How We Work'" :subtitle="'From your first call to launch, in four simple steps'" />

    <div ref="timeline" class="process-timeline container">
      <div class="timeline-track" aria-hidden="true">
        <div class="timeline-fill" :style="{ transform: `scaleY(${progress})` }"></div>
      </div>

      <ol class="process-steps">
        <li
          v-for="(step, index) in steps"
          :key="step.title"
          ref="rows"
          class="process-step"
          :class="{ 'is-even': index % 2 === 1, 'is-active': index < activeCount }"
        >
          <span
            class="step-number-bg"
            aria-hidden="true"
            :style="{ transform: `translateY(${shifts[index] || 0}px)` }"
          >{{ String(index + 1).padStart(2, '0') }}</span>

          <div class="step-marker" data-aos="zoom-in">
            <div class="step-dot">
              <i :class="step.icon"></i>
            </div>
          </div>

          <div class="step-card" :data-aos="index % 2 === 1 ? 'fade-left' : 'fade-right'">
            <p class="step-label">Step {{ index + 1 }}</p>
            <h4 class="step-title">{{ step.title }}</h4>
            <p class="step-desc">{{ step.desc }}</p>
          </div>
        </li>
      </ol>
    </div>

    <div class="text-center process-cta-wrap" data-aos="fade-up">
      <a :href="discoveryCallLink" class="process-cta">
        Start with a Quick Discovery Call <i class="fa-solid fa-arrow-right"></i>
      </a>
    </div>
  </section>
</template>

<script>
import Heading from "./common/heading.vue";

// How far the big step numbers drift relative to the page while scrolling.
const PARALLAX_STRENGTH = 0.25;
// Cap on that drift in pixels, so numbers never wander far from their step.
const MAX_SHIFT = 90;
// A step lights up once it crosses this point of the viewport (0 = top, 1 = bottom).
const ACTIVATION_LINE = 0.6;

export default {
  name: "Process",
  components: {
    Heading,
  },
  data() {
    return {
      discoveryEmail: 'arjadgohar14@gmail.com',
      progress: 0,
      activeCount: 0,
      shifts: [],
      steps: [
        {
          title: 'Discovery Call',
          icon: 'fa-solid fa-phone',
          desc: 'Book a quick call. We learn about your business, your goals, and what you need built.'
        },
        {
          title: 'Proposal & Plan',
          icon: 'fa-solid fa-file-signature',
          desc: 'We send a clear proposal with the scope, timeline, and cost, so you know exactly what you are getting.'
        },
        {
          title: 'Design & Build',
          icon: 'fa-solid fa-code',
          desc: 'We design and build your project, sharing progress with you along the way.'
        },
        {
          title: 'Launch & Support',
          icon: 'fa-solid fa-rocket',
          desc: 'We test everything with you, launch it, and stay on hand for fixes and updates.'
        }
      ]
    };
  },
  computed: {
    discoveryCallLink() {
      const subject = encodeURIComponent('Quick discovery call');
      return `mailto:${this.discoveryEmail}?subject=${subject}`;
    }
  },
  mounted() {
    this.reducedMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;
    this.ticking = false;
    this.onScroll = () => {
      if (!this.ticking) {
        this.ticking = true;
        window.requestAnimationFrame(this.update);
      }
    };
    window.addEventListener('scroll', this.onScroll, { passive: true });
    window.addEventListener('resize', this.onScroll);
    this.update();
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.onScroll);
    window.removeEventListener('resize', this.onScroll);
  },
  methods: {
    update() {
      this.ticking = false;
      const timeline = this.$refs.timeline;
      if (!timeline) return;

      const viewportHeight = window.innerHeight;
      const activationY = viewportHeight * ACTIVATION_LINE;
      const box = timeline.getBoundingClientRect();
      this.progress = Math.min(1, Math.max(0, (activationY - box.top) / box.height));

      const rows = this.$refs.rows || [];
      this.activeCount = rows.filter((row) => {
        const rowBox = row.getBoundingClientRect();
        return rowBox.top + rowBox.height / 2 <= activationY;
      }).length;

      if (this.reducedMotion) return;
      // Measure the rows (not the numbers) so the numbers' own movement never feeds back in.
      this.shifts = rows.map((row) => {
        const rowBox = row.getBoundingClientRect();
        const distanceFromCenter = rowBox.top + rowBox.height / 2 - viewportHeight / 2;
        const shift = distanceFromCenter * -PARALLAX_STRENGTH;
        return Math.round(Math.max(-MAX_SHIFT, Math.min(MAX_SHIFT, shift)));
      });
    }
  }
};
</script>

<style scoped>
.process-section {
  padding: 2rem 0 4rem;
}

.process-timeline {
  position: relative;
  max-width: 1000px;
  padding-top: 1rem;
  padding-bottom: 1rem;
}

.timeline-track {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 50%;
  width: 4px;
  transform: translateX(-50%);
  border-radius: 4px;
  background: rgba(17, 24, 39, 0.08);
  overflow: hidden;
}

.timeline-fill {
  width: 100%;
  height: 100%;
  transform-origin: top;
  background: linear-gradient(180deg, var(--color-primary), var(--color-secondary));
}

.process-steps {
  list-style: none;
  margin: 0;
  padding: 0;
}

.process-step {
  position: relative;
  display: grid;
  grid-template-columns: 1fr 72px 1fr;
  align-items: center;
  margin-bottom: 4.5rem;
}

.process-step:last-child {
  margin-bottom: 0;
}

/* Odd steps: card on the left, number on the right. Even steps swap sides. */
.step-card { grid-column: 1; grid-row: 1; }
.step-marker { grid-column: 2; grid-row: 1; justify-self: center; }
.step-number-bg { grid-column: 3; grid-row: 1; }

.process-step.is-even .step-card { grid-column: 3; }
.process-step.is-even .step-number-bg { grid-column: 1; justify-self: end; }

.step-card {
  background: #ffffff;
  border: 1px solid rgba(17, 24, 39, 0.08);
  border-radius: 20px;
  padding: 1.75rem;
  box-shadow: 0 10px 30px rgba(17, 24, 39, 0.06);
  transition: border-color 0.4s ease, box-shadow 0.4s ease;
}

.process-step.is-active .step-card {
  border-color: rgba(var(--color-primary-rgb), 0.35);
  box-shadow: 0 14px 36px rgba(var(--color-primary-rgb), 0.14);
}

.step-label {
  font-size: 0.8rem;
  font-weight: 700;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--color-secondary);
  margin-bottom: 0.35rem;
}

.step-title {
  font-size: 1.3rem;
  font-weight: 700;
  color: #111827;
  margin-bottom: 0.5rem;
}

.step-desc {
  font-size: 0.98rem;
  line-height: 1.6;
  color: #4b5563;
  margin: 0;
}

.step-dot {
  position: relative;
  z-index: 1;
  width: 56px;
  height: 56px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #ffffff;
  border: 3px solid rgba(17, 24, 39, 0.12);
  color: #9ca3af;
  font-size: 1.2rem;
  transition: background-color 0.4s ease, border-color 0.4s ease, color 0.4s ease, transform 0.4s ease, box-shadow 0.4s ease;
}

.process-step.is-active .step-dot {
  background: var(--color-primary);
  border-color: var(--color-primary);
  color: #ffffff;
  transform: scale(1.1);
  box-shadow: 0 0 0 8px rgba(var(--color-primary-rgb), 0.15);
}

.step-number-bg {
  padding: 0 2rem;
  font-family: 'Outfit', 'Inter', sans-serif;
  font-size: 7rem;
  font-weight: 800;
  line-height: 1;
  color: rgba(var(--color-primary-rgb), 0.12);
  user-select: none;
  will-change: transform;
  transition: color 0.4s ease;
}

.process-step.is-active .step-number-bg {
  color: rgba(var(--color-secondary-rgb), 0.18);
}

.process-cta-wrap {
  margin-top: 3.5rem;
}

.process-cta {
  display: inline-flex;
  align-items: center;
  gap: 0.6rem;
  padding: 0.95rem 2rem;
  border-radius: 50px;
  background: var(--color-primary);
  color: #ffffff;
  font-weight: 700;
  text-decoration: none;
  transition: background-color 0.3s ease, transform 0.3s ease;
}

.process-cta:hover {
  background: var(--color-secondary);
  color: #ffffff;
  text-decoration: none;
  transform: translateY(-2px);
}

/* Phones and small tablets: one column, line on the left, no big numbers. */
@media screen and (max-width: 767.98px) {
  .timeline-track {
    left: 43px;
  }

  .process-step {
    grid-template-columns: 56px 1fr;
    column-gap: 1rem;
    margin-bottom: 2.5rem;
  }

  .step-marker,
  .process-step.is-even .step-marker {
    grid-column: 1;
  }

  .step-card,
  .process-step.is-even .step-card {
    grid-column: 2;
    padding: 1.25rem;
  }

  .step-number-bg {
    display: none;
  }
}
</style>
