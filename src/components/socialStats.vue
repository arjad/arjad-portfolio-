<template>
  <section class="social-stats-section py-5 my-5" id="social_stats">
    <div class="container text-center">
      <h3 class="mb-5 section-title" data-aos="fade-up">My Community</h3>
      
      <div class="profile-container d-flex flex-column align-items-center justify-content-center" data-aos="zoom-in">
        <div class="profile-image-wrapper mb-4">
          <img src="/me.png" alt="Arjad" class="profile-img shadow-lg" />
        </div>
        
        <div class="stats-grid mt-4 w-100">
          <a href="https://www.linkedin.com/in/arjad/" target="_blank" class="stat-card text-decoration-none" data-aos="fade-up" data-aos-delay="100">
            <i class="fab fa-linkedin stat-icon linkedin-color"></i>
            <h4>5K</h4>
            <p>Followers</p>
            <span class="username">@arjad</span>
          </a>

          <a href="https://www.instagram.com/arjad.codes/" target="_blank" class="stat-card text-decoration-none" data-aos="fade-up" data-aos-delay="200">
            <i class="fab fa-instagram stat-icon instagram-color"></i>
            <h4>450</h4>
            <p>Followers</p>
            <span class="username">@arjad.codes</span>
          </a>

          <a href="https://www.youtube.com/@arjadcodes" target="_blank" class="stat-card text-decoration-none" data-aos="fade-up" data-aos-delay="300">
            <i class="fab fa-youtube stat-icon youtube-color"></i>
            <h4>100</h4>
            <p>Subscribers</p>
            <span class="username">@arjadcodes</span>
          </a>

          <a href="https://www.tiktok.com/@arjad.code?lang=en" target="_blank" class="stat-card text-decoration-none" data-aos="fade-up" data-aos-delay="400">
            <i class="fab fa-tiktok stat-icon tiktok-color"></i>
            <h4>50</h4>
            <p>Followers</p>
            <span class="username">@arjad.code</span>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "SocialStats"
};
</script>

<style scoped>
.social-stats-section {
  position: relative;
  z-index: 10;
}

.section-title {
  font-size: 2.5rem;
  font-weight: 700;
  color: #42b883;
}

.profile-image-wrapper {
  width: 180px;
  height: 180px;
  border-radius: 50%;
  padding: 8px;
  background: linear-gradient(135deg, #42b883, #35495e);
  display: inline-block;
}

.profile-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 50%;
  border: 4px solid #fff;
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 2rem;
  max-width: 1000px;
  margin: 0 auto;
}

.stat-card {
  background: rgba(255, 255, 255, 0.03);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 20px;
  padding: 2rem 1rem;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.stat-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
  background: rgba(255, 255, 255, 0.05);
}

.stat-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.linkedin-color { color: #0a66c2; }
.instagram-color { color: #e1306c; }
.youtube-color { color: #ff0000; }
.tiktok-color { color: #000000; }

.dark-mode .tiktok-color { color: #ffffff; }
.dark-mode .profile-img { border-color: #1a1a1a; }

.stat-card h4 {
  font-size: 2rem;
  font-weight: 800;
  margin: 0;
  color: #333;
}

.dark-mode .stat-card h4 {
  color: #fff;
}

.stat-card p {
  color: #666;
  text-transform: uppercase;
  font-size: 0.85rem;
  letter-spacing: 2px;
  margin-bottom: 0.5rem;
}

.dark-mode .stat-card p {
  color: #aaa;
}

.username {
  font-weight: 600;
  color: #42b883;
  font-size: 0.95rem;
}
</style>
