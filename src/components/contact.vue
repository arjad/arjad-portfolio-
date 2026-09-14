<template>
  <div>
    <footer class="footer-compact py-5" id="contact">
      <div class="container">
        <div class="row align-items-center">
          <div class="col-md-6 mb-4 mb-md-0 d-flex flex-column align-items-center align-items-md-start">
            <h5 class="mb-3 accent-primary">Navigation</h5>
            <ul class="list-unstyled d-flex flex-column gap-4 text-center text-md-start">
              <li><router-link to="/" class="nav-link-footer">Home</router-link></li>
              <li><router-link to="/projects" class="nav-link-footer">Projects</router-link></li>
              <li><a href="#about" class="nav-link-footer">About</a></li>
              <li><a href="#contact" class="nav-link-footer">Contact</a></li>
            </ul>
          </div>
          <div class="col-md-6 d-flex flex-column align-items-center align-items-md-start ps-md-5 mt-5 mt-md-0">
            <h5 class="mb-3 accent-primary">Connect with me</h5>
            <ul class="list-unstyled socials-grid text-center text-md-start socials-footer w-100">
              <li><a href="https://www.instagram.com/arjad.codes/" target="_blank" class="social-link-full"><i class="fab fa-instagram mr-2"></i> Instagram</a></li>
              <li><a href="https://www.linkedin.com/in/arjad/" target="_blank" class="social-link-full"><i class="fab fa-linkedin mr-2"></i> LinkedIn</a></li>
              <li><a href="https://github.com/arjad" target="_blank" class="social-link-full"><i class="fab fa-github mr-2"></i> GitHub</a></li>
              <li><a href="mailto:arjadgohar14@gmail.com" class="social-link-full"><i class="fas fa-envelope mr-2"></i> Email</a></li>
              <li><a href="https://www.tiktok.com/@arjad.code?lang=en" target="_blank" class="social-link-full"><i class="fab fa-tiktok mr-2"></i> TikTok</a></li>
              <li><a href="https://www.youtube.com/@arjadcodes" target="_blank" class="social-link-full"><i class="fab fa-youtube mr-2"></i> YouTube</a></li>
            </ul>
          </div>
        </div>
        <div class="row mt-4 pt-4 border-top border-secondary border-opacity-25">
          <div class="col-12 text-center copyright">
            © 2026 Arjad Gohar. Built with <a href="https://github.com/arjad/Portfolio" target="_blank" class="accent-primary">Vue.js</a>
          </div>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  name: "FooterComponent"
};
</script>

<style scoped>
.footer-compact {
  background: rgba(0, 0, 0, 0.03);
  backdrop-filter: blur(8px);
  -webkit-backdrop-filter: blur(8px);
  border-top: 1px solid rgba(0, 0, 0, 0.08);
  width: 100%;
  margin-top: 6rem;
}

.copyright {
  color: rgba(0, 0, 0, 0.6);
  font-size: 0.9rem;
}

.accent-primary {
  color: #42b883;
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s ease;

  &:hover {
    color: #35495e;
    text-decoration: underline;
  }
}

.socials-footer {
  gap: 1.25rem;
}

.social-link {
  color: rgba(0, 0, 0, 0.6);
  font-size: 1.15rem;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;

  &:hover {
    color: #42b883;
    transform: translateY(-2px);
    text-shadow: 0 0 10px rgba(66, 184, 131, 0.5);
  }
}

.social-link-full {
  color: rgba(0, 0, 0, 0.6);
  font-size: 1rem;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  text-decoration: none;

  i {
    margin-right: 0.5rem !important; /* Explicitly guarantee margin right */
  }

  &:hover {
    color: #42b883;
    transform: translateX(-3px);
  }
}

.nav-link-footer {
  color: rgba(0, 0, 0, 0.6);
  text-decoration: none;
  font-size: 1rem;
  transition: color 0.3s ease;

  &:hover {
    color: #42b883;
  }
}

.footer-compact ul li {
  margin-bottom: 0.6rem; /* Explicit vertical spacing */
}
.footer-compact ul li:last-child {
  margin-bottom: 0;
}

.socials-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  row-gap: 0.6rem;
  column-gap: 1.5rem;
}

@media (max-width: 576px) {
  .socials-grid {
    grid-template-columns: 1fr; /* Stack on very small screens if needed, but 2 cols might be fine. Let's keep 2 cols */
    grid-template-columns: 1fr 1fr; 
  }
}
</style>

<style lang="scss">
.dark-mode {
  .footer-compact {
    background: rgba(40, 40, 40, 0.4) !important;
    border-top: 1px solid rgba(255, 255, 255, 0.08) !important;
  }
  .copyright, .social-link, .social-link-full, .nav-link-footer {
    color: rgba(255, 255, 255, 0.6) !important;
  }
  .nav-link-footer:hover, .social-link-full:hover {
    color: #42b883 !important;
  }
}
</style>

