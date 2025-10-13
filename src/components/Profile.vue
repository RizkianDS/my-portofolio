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
          <div class="category-tags">
            <span class="tag">HR</span>
            <span class="tag">Sekretaris</span>
            <span class="tag">Administration</span>
            <span class="tag">IT</span>
          </div>
          <a 
            href="https://drive.google.com/file/d/1JyfO5oBMfC0_nkFy7Pnn_rCldekawxnX/view" 
            target="_blank" 
            rel="noopener noreferrer"
            class="cv-button"
          >
            Lihat CV
          </a>
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

<style scoped>
#profile {
  background-color: transparent; 
  padding: 6rem 2rem;
  overflow-x: hidden; 
}

.profile-container {
  margin: 0 auto;
  margin-top: 2rem;
  width: 100%;
  box-sizing: border-box;
}

.profile-card {
  background-color: #edf2f7; /* Off-white background */
  border-radius: 15px;
  display: flex;
  align-items: center;
  gap: 2rem;
  padding: 2rem;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.3);
  width: 100%;
  box-sizing: border-box;
  
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
  width: 250px; /* Keep the width */
  height: 350px; /* Adjust height to be automatic */
  border-radius: 10px;
  overflow: hidden;
}

.profile-image-container img {
  width: 100%;
  height: 230%;
  object-fit: cover; /* Cover will now work correctly without cropping */
  display: block; /* Remove any extra space below the image */
}

.profile-info {
    text-align: center; /* Center align all text within the info section */
    display: flex;
    flex-direction: column;
    align-items: center;
}

.profile-info h2 {
  color: #16a085;
  font-size: 2rem;
  margin-top: 0;
}

.profile-info p {
  color: #2d3748; /* Dark gray text for readability on light background */
  line-height: 1.6;
}

.category-tags {
  margin-top: 1.5rem;
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
  justify-content: center; /* Center the tags */
}

.tag {
  display: inline-block;
  padding: 0.5rem 1rem;
  border: 1px solid #cbd5e0;
  border-radius: 20px;
  font-size: 0.875rem;
  font-weight: 500;
  color: #4a5568;
  background-color: #fff;
  transition: all 0.3s ease;
}

.tag:hover {
  background-color: #16a085;
  color: #fff;
  border-color: #16a085;
  transform: translateY(-2px);
  box-shadow: 0 4px 10px rgba(22, 160, 133, 0.3);
}

.cv-button {
  margin-top: 2rem; /* Space above the button */
  background-color: #16a085;
  color: white;
  padding: 0.75rem 1.75rem;
  border-radius: 50px;
  text-decoration: none;
  font-size: 1rem;
  font-weight: 800;
  transition: background-color 0.3s ease, transform 0.3s ease, box-shadow 0.3s ease;
  box-shadow: 0 4px 15px rgba(22, 160, 133, 0.4);
  display: inline-block;
  border: none;
  font-family: 'Poppins', sans-serif;
  cursor: pointer;
}

.cv-button:hover {
  background-color: #19b698;
  transform: translateY(-4px);
  box-shadow: 0 6px 20px rgba(22, 160, 133, 0.5);
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .profile-card {
    flex-direction: column;
    text-align: center;
  }

  .profile-image-container {
    width: 200px;
    height: auto;
  }

}
</style>