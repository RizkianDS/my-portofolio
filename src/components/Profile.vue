<template>
  <section id="profile">
    <div class="profile-container">
      <div ref="profileCard" class="profile-card" :class="{ 'is-visible': isCardVisible }">
        <div class="profile-image-container">
          <img src="/foto.png" alt="Foto Profil">
        </div>
        <div class="profile-info">
          <h2>Tentang Saya</h2>
          <p>
            Saya adalah seorang pengembang web dengan pengalaman dalam menciptakan aplikasi web yang modern dan responsif. Saya bersemangat tentang teknologi dan selalu berusaha untuk mempelajari hal-hal baru.
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const profileCard = ref(null);
const isCardVisible = ref(false);

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          isCardVisible.value = true;
          observer.unobserve(entry.target); // Stop observing after animation triggers
        }
      });
    },
    {
      threshold: 0.1 // Trigger when 10% of the element is visible
    }
  );

  if (profileCard.value) {
    observer.observe(profileCard.value);
  }
});
</script>

<style>
#profile {
  background-color: transparent;
  padding: 6rem 2rem;
  overflow-x: hidden; /* Prevent horizontal scrollbar issues during animation */
}

.profile-container {
  margin: 0 auto;
  margin-top: 2rem;
  width: 100%;
  box-sizing: border-box;
}

.profile-card {
  background-color: #1a202c;
  border-radius: 15px;
  display: flex;
  align-items: center;
  gap: 2rem;
  padding: 2rem;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.3);
  width: 100%;
  box-sizing: border-box;
  
  /* Animation styles */
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.8s ease-out, transform 0.8s ease-out;
}

.profile-card.is-visible {
  opacity: 1;
  transform: translateY(0);
}

.profile-image-container {
  flex-shrink: 0;
  width: 250px;
  height: 350px;
  border-radius: 10px;
  overflow: hidden;
}

.profile-image-container img {
  width: 100%;
  height: 230%;
  object-fit: cover;
  object-position: center 30%;
  transform: scale(1.2);
}

.profile-info h2 {
  color: #16a085;
  font-size: 2rem;
  margin-top: 0;
}

.profile-info p {
  color: #a0aec0;
  line-height: 1.6;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .profile-card {
    flex-direction: column;
    text-align: center;
  }

  .profile-image-container {
    width: 200px;
    height: 280px;
  }
}
</style>
