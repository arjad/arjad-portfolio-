<template>
    <div id="write_me">
        <Heading :title="'Contact Us'" :subtitle="'Let\'s work together! Feel free to reach out via email or social media'" />
        <div class="container container-div" data-aos="fade-up">
            <div class="contact-cta-container text-center d-flex flex-column align-items-center justify-content-center p-4">
                <p class="cta-desc mb-4">Tell us what you're building. We take on web, app, and AI projects for businesses of all sizes.</p>
                <a href="mailto:arjadgohar14@gmail.com" class="upwork-cta-btn email-cta-btn">
                    <i class="fas fa-envelope me-2"></i> Email Us
                </a>
            </div>
        </div>
    </div>
</template>

<script>
import Heading from "./common/heading.vue";
export default {
  components: {
    Heading,
  },
}
</script>

<style lang="scss" scoped>

.container-div {
  border: none;
  box-shadow: none;
  width: 100%;
  max-width: 1050px;
  border-radius: 24px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.contact-cta-container {
  height: 90%;
  width: 450px;
  max-width: 90%;
}

.cta-desc {
  font-size: 1.05rem;
  color: #6b7280;
  line-height: 1.6;
}

.upwork-cta-btn, .email-cta-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  background: var(--color-primary);
  color: #ffffff;
  font-size: 1.1rem;
  font-weight: 700;
  padding: 1rem 2rem;
  border-radius: 50px;
  text-decoration: none;
  transition: all 0.3s ease;
  box-shadow: 0 6px 20px rgba(var(--color-primary-rgb), 0.3);

  i {
    margin-left: 0.5rem;
    margin-right: 0.5rem;
  }

  &:hover {
    background: var(--color-secondary);
    color: #ffffff;
    transform: translateY(-3px);
    box-shadow: 0 10px 25px rgba(var(--color-secondary-rgb), 0.5);
    text-decoration: none;
  }
}

@media screen and (max-width: 768px) {
  .container-div {
    flex-direction: column !important;
    height: auto !important;
    min-height: auto !important;
    width: 100% !important;
    padding: 1rem 0.5rem !important;
  }

  .contact-cta-container {
    width: 100% !important;
    max-width: 100% !important;
    height: auto !important;
    padding: 1rem 0.5rem !important;
  }

  .cta-desc {
    font-size: 1rem !important;
  }

  .upwork-cta-btn, .email-cta-btn {
    width: 90% !important;
    padding: 0.85rem 1.5rem !important;
    font-size: 1rem !important;
  }
}
</style>
