<template>
  <section id="home" class="hero">
    <div class="hero-content">
      <h1 class="hero-title" :class="{ 'is-visible': isTitleVisible }">Rizkian Dili Septyanto</h1>
      <p class="hero-subtitle">
        {{ typedText }}<span class="cursor"></span>
      </p>
      <a href="#profile" class="hero-button">Lihat Profil Saya</a>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const isTitleVisible = ref(false);
const typedText = ref('');
const phrases = ["Web Developer", "Human Capital", "Sekretaris", "Adminstration"];
let phraseIndex = 0;
let charIndex = 0;
let isDeleting = false;

const typingSpeed = 150;
const erasingSpeed = 100;
const delayBetweenPhrases = 2000;

const typewriter = () => {
  const currentPhrase = phrases[phraseIndex];
  let timeout = isDeleting ? erasingSpeed : typingSpeed;

  if (isDeleting) {
    typedText.value = currentPhrase.substring(0, charIndex - 1);
    charIndex--;
  } else {
    typedText.value = currentPhrase.substring(0, charIndex + 1);
    charIndex++;
  }

  if (!isDeleting && charIndex === currentPhrase.length) {
    isDeleting = true;
    timeout = delayBetweenPhrases;
  } else if (isDeleting && charIndex === 0) {
    isDeleting = false;
    phraseIndex = (phraseIndex + 1) % phrases.length;
  }

  setTimeout(typewriter, timeout);
};

onMounted(() => {
  setTimeout(() => {
    isTitleVisible.value = true;
  }, 200);
  setTimeout(typewriter, 800);
});
</script>

<style>
/* Ensure the hero section itself has no padding to allow edge-to-edge background */
#home.hero {
  padding: 0;
}

.hero {
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  height: 100vh;
  color: white;
  position: relative;
  background-image: url('/bg.jpg');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  box-sizing: border-box; /* Better box model handling */
}

.hero::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0; bottom: 0;
  background: transparent;
  z-index: 1;
}

/* Re-introduce padding to the content container */
.hero-content {
  position: relative;
  z-index: 2;
  max-width: 1200px; /* Optional: constrain content width on very large screens */
  padding: 0 2rem; /* Restore horizontal padding */
  display: flex;
  flex-direction: column;
  align-items: center;
}

.hero-title {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.8s ease-out, transform 0.8s ease-out;
  font-size: 3.5rem;
  font-weight: 700;
  margin-bottom: 1rem;
  text-shadow: 0 4px 15px rgba(0,0,0,0.5), 0 0 10px rgba(22, 160, 133, 0.5);
}

.hero-title.is-visible {
  opacity: 1;
  transform: translateY(0);
}

.hero-subtitle {
  font-size: 1.5rem;
  font-weight: 400;
  margin-bottom: 2rem;
  color: #e2e8f0;
  text-shadow: 0 2px 10px rgba(0,0,0,0.5), 0 0 5px rgba(22, 160, 133, 0.4);
  height: 2.2rem; /* Fixed height to prevent vertical jank */
}

.cursor {
  display: inline-block;
  width: 3px;
  height: 1.5rem;
  background-color: #16a085;
  animation: blink 1s infinite;
  margin-left: 4px;
  vertical-align: middle;
}

@keyframes blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0; }
}

.hero-button {
  background-color: #16a085;
  color: white;
  padding: 1rem 2.5rem;
  border-radius: 50px;
  text-decoration: none;
  font-size: 1.1rem;
  font-weight: 600;
  transition: background-color 0.3s ease, transform 0.3s ease;
  box-shadow: 0 5px 15px rgba(22, 160, 133, 0.4);
}

.hero-button:hover {
  background-color: #19b698;
  transform: translateY(-3px);
}

@media (max-width: 768px) {
  .hero-content {
    padding: 0 1rem; /* Adjust padding for smaller screens */
  }
  .hero-title {
    font-size: 2.5rem;
  }
  .hero-subtitle {
    font-size: 1.2rem;
    height: 1.8rem;
  }
  .cursor {
    height: 1.2rem;
  }
}
</style>
