<template>
  <div id="navigation" class="nav-container">
    <div class="navbar-bar d-flex justify-content-between align-items-center">
      <!-- Profile Brand -->
      <div class="profile-brand d-flex align-items-center" @click="scrollToSection('summary')">
        <img src="/logo.png" alt="" class="brand-logo" />
        <span class="profile-name">Right Click Solutions</span>
      </div>

      <!-- Desktop Nav Links (Hidden on Mobile) -->
      <ul class="d-none d-md-flex mb-0 align-items-center nav-links">
        <li class="p-2 scroll-to" @click="scrollToSection('about')">About</li>
        <li class="p-2 scroll-to" @click="scrollToSection('services')">Services</li>
        <li class="p-2 scroll-to" @click="scrollToSection('projects')">Projects</li>
        <li class="p-2 scroll-to" @click="scrollToSection('contact')">Contact</li>
      </ul>

      <!-- Mobile Hamburger Toggle Button -->
      <button class="hamburger-btn d-flex d-md-none align-items-center justify-content-center" @click="isMenuOpen = true" aria-label="Open Navigation Menu">
        <i class="fa-solid fa-bars"></i>
      </button>
    </div>

    <!-- Mobile Side Popup Drawer -->
    <transition name="slide-side">
      <div v-if="isMenuOpen" class="mobile-drawer">
        <div class="drawer-header d-flex justify-content-between align-items-center p-4 border-bottom border-secondary border-opacity-25">
          <span class="drawer-title">Right Click Solutions</span>
          <button class="close-btn" @click="isMenuOpen = false" aria-label="Close Navigation Menu">
            <i class="fa-solid fa-xmark"></i>
          </button>
        </div>

        <ul class="drawer-links list-unstyled p-4 mb-0">
          <li class="drawer-item py-3 border-bottom border-secondary border-opacity-25 d-flex align-items-center" @click="handleMobileNav('about')">
            <i class="fa-solid fa-user me-3 text-muted"></i><span>About</span>
          </li>
          <li class="drawer-item py-3 border-bottom border-secondary border-opacity-25 d-flex align-items-center" @click="handleMobileNav('services')">
            <i class="fa-solid fa-code me-3 text-muted"></i><span>Services</span>
          </li>
          <li class="drawer-item py-3 border-bottom border-secondary border-opacity-25 d-flex align-items-center" @click="handleMobileNav('projects')">
            <i class="fa-solid fa-briefcase me-3 text-muted"></i><span>Projects</span>
          </li>
          <li class="drawer-item py-3 border-bottom border-secondary border-opacity-25 d-flex align-items-center" @click="handleMobileNav('contact')">
            <i class="fa-solid fa-envelope me-3 text-muted"></i><span>Contact</span>
          </li>
        </ul>
      </div>
    </transition>

    <!-- Backdrop Overlay for Mobile Drawer -->
    <transition name="fade">
      <div v-if="isMenuOpen" class="drawer-backdrop" @click="isMenuOpen = false"></div>
    </transition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isMenuOpen: false
    };
  },
  methods: {
    handleMobileNav(sectionId) {
      this.isMenuOpen = false;
      this.scrollToSection(sectionId);
    },
    scrollToSection(sectionId) {
      if (this.$route.path !== '/') {
        this.$router.push({ path: '/', hash: '#' + sectionId });
      } else {
        const element = document.getElementById(sectionId);
        if (element) {
          element.scrollIntoView({ behavior: 'smooth' });
        }
      }
    }
  },
};
</script>

<style lang="scss" scoped>
.nav-container {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
}

.navbar-bar {
  background: rgba(255, 255, 255, 0.85);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  border-bottom: 1px solid rgba(17, 24, 39, 0.08);
  padding: 0.9rem 2rem;
  width: 100%;
  box-shadow: 0 4px 20px 0 rgba(17, 24, 39, 0.06);
  transition: all 0.3s ease;
}

.profile-brand {
  cursor: pointer;
  gap: 0.75rem;

  .brand-logo {
    width: 38px;
    height: 38px;
    object-fit: contain;
  }

  .profile-name {
    color: #111827;
    font-weight: 700;
    font-size: 1.1rem;
    letter-spacing: -0.02em;
  }
}

.nav-links {
  list-style: none;
  gap: 1.5rem;

  li.scroll-to {
    color: #374151;
    font-size: 0.95rem;
    font-weight: 500;
    transition: all 0.3s ease;
    cursor: pointer;
    position: relative;

    &:hover {
      color: var(--color-primary);
    }
  }
}

.hamburger-btn {
  background: rgba(17, 24, 39, 0.05);
  border: 1px solid rgba(17, 24, 39, 0.15);
  color: #111827;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  font-size: 1.1rem;
  cursor: pointer;
  transition: all 0.3s ease;

  &:hover {
    background: rgba(17, 24, 39, 0.1);
  }
}

.mobile-drawer {
  position: fixed;
  top: 0;
  right: 0;
  width: 290px;
  max-width: 85vw;
  height: 100vh;
  background: #ffffff;
  border-left: 1px solid rgba(17, 24, 39, 0.08);
  box-shadow: -10px 0 30px rgba(17, 24, 39, 0.15);
  z-index: 2000;
  display: flex;
  flex-direction: column;
}

.drawer-title {
  color: #111827;
  font-weight: 700;
  font-size: 1.1rem;
}

.drawer-header {
  .close-btn {
    background: transparent;
    border: none;
    color: #111827;
    font-size: 1.4rem;
    cursor: pointer;
    padding: 0.5rem;
    transition: transform 0.2s ease;

    &:hover {
      transform: scale(1.15);
    }
  }
}

.drawer-item {
  color: #374151;
  font-size: 1.1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.25s ease;

  i {
    margin-right: 1.25rem !important;
    width: 22px;
    text-align: center;
  }

  &:hover {
    color: var(--color-primary);
    padding-left: 0.5rem;
  }
}

.drawer-backdrop {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgba(17, 24, 39, 0.35);
  backdrop-filter: blur(4px);
  z-index: 1999;
}

.slide-side-enter-active, .slide-side-leave-active {
  transition: transform 0.35s cubic-bezier(0.4, 0, 0.2, 1);
}
.slide-side-enter, .slide-side-leave-to {
  transform: translateX(100%);
}

@media screen and (max-width: 768px) {
  .navbar-bar {
    padding: 0.8rem 1.25rem;
  }
}
</style>
