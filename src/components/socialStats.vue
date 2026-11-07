<template>
  <section class="social-stats-section py-5 my-3" id="social_stats">
    <div class="container text-center">
      <Heading :title="'Meet the Founder'" :subtitle="'Arjad Gohar leads Right Click Solutions. See the journey behind the agency and follow along on social media'" />
      
      <div class="profile-container d-flex flex-column align-items-center justify-content-center">
        
    <div class="gallery-div">
      <div id="gallery">
        <div>
          <img data-aos="zoom-in" data-aos-delay="0" zoomtastic src="../assets/journey/meee.jpeg" alt="profile pic" />
        </div>
        <div>
          <img data-aos="zoom-in" data-aos-delay="80" zoomtastic src="../assets/journey/desk.jpg" alt="profile pic" />
          <a href="#lightbox-2">Work Desk</a>
        </div>
        <div>
          <img data-aos="zoom-in" data-aos-delay="160" zoomtastic src="../assets/journey/me2.jpg" alt="profile pic" />
        </div>
        <div>
          <img data-aos="zoom-in" data-aos-delay="240" zoomtastic src="../assets/journey/me5.jpeg" alt="profile pic" />
          <a href="#lightbox-4">Tour</a>
        </div>
        <div>
          <img data-aos="zoom-in" data-aos-delay="320" zoomtastic src="../assets/journey/me1.jpg" alt="profile pic" />
        </div>
        <div>
          <img data-aos="zoom-in" data-aos-delay="400" zoomtastic src="../assets/journey/laptop.jpeg" alt="profile pic" />
          <a href="#lightbox-4">mac</a>
        </div>

      </div>
      
    </div>



        <Journey class="mt-3" />

        <div class="stats-grid mt-5 w-100">
          <div data-aos="fade-up" data-aos-delay="100">
          <a href="https://www.linkedin.com/in/arjad/" target="_blank" class="stat-card text-decoration-none h-100">
            <i class="fab fa-linkedin stat-icon linkedin-color"></i>
            <h4>5K</h4>
            <p>Followers</p>
            <span class="username">@arjad</span>
          </a>
          </div>

          <div data-aos="fade-up" data-aos-delay="200">
          <a href="https://www.instagram.com/arjad.codes/" target="_blank" class="stat-card text-decoration-none h-100">
            <i class="fab fa-instagram stat-icon instagram-color"></i>
            <h4>450</h4>
            <p>Followers</p>
            <span class="username">@arjad.codes</span>
          </a>
          </div>

          <div data-aos="fade-up" data-aos-delay="300">
          <a href="https://www.youtube.com/@arjadcodes" target="_blank" class="stat-card text-decoration-none h-100">
            <i class="fab fa-youtube stat-icon youtube-color"></i>
            <h4>100</h4>
            <p>Subscribers</p>
            <span class="username">@arjadcodes</span>
          </a>
          </div>

          <div data-aos="fade-up" data-aos-delay="400">
          <a href="https://www.tiktok.com/@arjad.code?lang=en" target="_blank" class="stat-card text-decoration-none h-100">
            <i class="fab fa-tiktok stat-icon tiktok-color"></i>
            <h4>50</h4>
            <p>Followers</p>
            <span class="username">@arjad.code</span>
          </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import Heading from "./common/heading.vue";
import Journey from "./journey.vue";

export default {
  name: "SocialStats",
  components: {
    Heading,
    Journey,
  },
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
  color: var(--color-primary);
}

.profile-image-wrapper {
  width: 180px;
  height: 180px;
  border-radius: 50%;
  padding: 8px;
  background: linear-gradient(135deg, var(--color-primary), var(--color-secondary));
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
  background: #ffffff;
  border: 1px solid rgba(17, 24, 39, 0.08);
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
}

.stat-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.linkedin-color { color: #0a66c2; }
.instagram-color { color: #e1306c; }
.youtube-color { color: #ff0000; }
.tiktok-color { color: #000000; }


.stat-card h4 {
  font-size: 2rem;
  font-weight: 800;
  margin: 0;
  color: #333;
}


.stat-card p {
  color: #666;
  text-transform: uppercase;
  font-size: 0.85rem;
  letter-spacing: 2px;
  margin-bottom: 0.5rem;
}


.username {
  font-weight: 600;
  color: var(--color-primary);
  font-size: 0.95rem;
}

.gallery-div {
  height:30rem;
  overflow: hidden;
}
#gallery {
  display: grid;
  height: 30rem;
  grid-template: repeat(3, 1fr)/repeat(6, 1fr);
  grid-gap: 0.5em;
}
#gallery > div:nth-child(6n+1) {
  grid-column: span 2;
  grid-row: span 2;
}
#gallery > div:nth-child(2) {
  grid-column: span 3;
  grid-row: span 3;
}
#gallery > div:nth-child(4) {
  grid-column: span 1;
  grid-row: span 2;
}
#gallery > div > a {
  opacity: 0;
  position: absolute;
  color: #000;
  background-color: #000;
  font: bold 4em "Helvetica";
  text-shadow: 0 -1px 5px #fff, -1px 0px 5px #fff, 0 1px 5px #fff, 1px 0px 5px #fff;
  padding: 2rem;
  width: 100%;
  height: 100%;
  transition: all ease 1s;
}
#gallery > div > img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: all ease 1s;
}
#gallery > div:hover img {
  filter: blur(4px);
}
#gallery > div:hover a {
  opacity: 1;
}
#gallery > div {
  overflow: hidden;
  position: relative;
  box-shadow: 0 2px 8px 0 rgba(0, 0, 0, 0.2), 0 3px 20px 0 rgba(0, 0, 0, 0.19);
}
#gallery div,
#gallery a {
  display: flex;
  justify-content: center;
  align-items: center;
  text-decoration: none;
}

@media (max-width: 800px) {
  .gallery-div {
    height: auto;
  }
  #gallery {
    height: auto;
    grid-template: none / 1fr 1fr;
  }
  #gallery > div,
  #gallery > div:nth-child(n) {
    grid-column: auto;
    grid-row: auto;
    height: 11rem;
  }
  #gallery > div > img {
    height: 100%;
    min-height: 0;
    object-fit: cover;
    object-position: top;
  }
}

[id^=lightbox-] {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  opacity: 0;
  transition: opacity 450ms ease-in-out;
  align-items: center;
  justify-content: center;
  pointer-events: none;
}
[id^=lightbox-]:target {
  opacity: 1;
  pointer-events: inherit;
}
[id^=lightbox-]:target img {
  filter: blur(0);
}
[id^=lightbox-] .content {
  max-width: 90%;
  position: relative;
  color: #fff;
}
[id^=lightbox-] .content:hover > a.close {
  opacity: 1;
  transform: scale(1, 1);
}
[id^=lightbox-] .content:hover > .title {
  opacity: 1;
  transform: translateY(-3px);
}
[id^=lightbox-] .content:hover > .title::after {
  opacity: 1;
}
[id^=lightbox-] .content > * {
  transition: all 450ms ease-in-out;
}
[id^=lightbox-] .title {
  display: block;
  margin: 0;
  padding: 1em;
  position: absolute;
  bottom: 0;
  width: 100%;
  transform: translateY(50%);
  font-size: 1.5em;
  opacity: 0;
}
[id^=lightbox-] .title::after {
  content: " ";
  background-color: rgba(0, 0, 0, 0.4);
  bottom: 0;
  left: 0;
  height: 100%;
  width: 100%;
  position: absolute;
  transition: all 350ms ease-in-out 250ms;
  opacity: 0;
  transform-origin: bottom;
  mix-blend-mode: soft-light;
}
[id^=lightbox-] img {
  max-height: 90vh;
  max-width: 100%;
  margin: 0;
  padding: 0;
  filter: blur(50px);
}
[id^=lightbox-] a.close {
  width: 2em;
  height: 2em;
  position: absolute;
  right: 0;
  top: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  transform: scale(0, 0);
  opacity: 0;
  transform-origin: right top;
  text-decoration: none;
  color: #fff;
}
[id^=lightbox-] a.close::after {
  content: "X";
}
</style>


