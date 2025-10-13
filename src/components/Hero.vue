<template>
  <div id="hero">
    <div class="hero-content">
      <h1 class="animate-fade-in-slide-up">Rizkian Dili Septyanto</h1>
      <p ref="typewriterEl" class="typewriter-text"></p>
      <button @click="handleScrollButtonClick" class="hero-button animate-fade-in-slide-up">Lihat Profil Saya</button>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, defineEmits } from 'vue';
import Typewriter from 'typewriter-effect/dist/core';

const emit = defineEmits(['scrollToSection']);

const typewriterEl = ref(null);

onMounted(() => {
  if (typewriterEl.value) {
    const typewriter = new Typewriter(typewriterEl.value, {
      loop: true,
      delay: 75,
      deleteSpeed: 50,
    });

    typewriter
      .pauseFor(500)
      .typeString('Human Capital')
      .pauseFor(2000)
      .deleteAll()
      .typeString('Sekretaris')
      .pauseFor(2000)
      .deleteAll()
      .typeString('Administration')
      .pauseFor(2000)
      .deleteAll()
      .typeString('Web Developer')
      .pauseFor(2500)
      .start();
  }
});

const handleScrollButtonClick = () => {
  emit('scrollToSection', '#profile');
};
</script>

<style scoped>
/* Keyframe animation for the fade-in and slide-up effect */
@keyframes fade-in-slide-up {
  0% {
    opacity: 0;
    transform: translateY(20px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}

#hero {
  position: relative;
  height: 100vh;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  background-image: url('/bg.jpg'); 
  background-size: cover;
  background-position: center;
  color: #fff;
  overflow: hidden;
  /* No padding needed here, we want it edge-to-edge */
}

.hero-content {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1.5rem; /* Space between elements */
}

.hero-content h1 {
  font-size: 4rem;
  margin: 0;
  color: #fff;
  text-shadow: 2px 2px 8px rgba(0, 0, 0, 0.7);
}

.typewriter-text {
  font-size: 2rem;
  color: #fff; /* Teal color */
  text-shadow: 2px 2px 8px rgba(0, 0, 0, 0.8);
  height: 2.5rem; /* Allocate space to prevent layout shift */
}

/* Styling for the typewriter cursor */
:deep(.Typewriter__cursor) {
  color: #fff; /* Match the text color #16a085 */
  font-size: 2rem;  /* Match the text size */
  animation: blink 1s infinite;
}

@keyframes blink {
  50% { opacity: 0; }
}

.hero-button {
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
  margin-top: 1rem; /* Add some space above the button */
  border: none; /* Remove default button border */
  font-family: 'Poppins', sans-serif; /* Ensure font consistency */
  cursor: pointer; /* Ensure cursor is a pointer */
}

.hero-button:hover {
  background-color: #19b698;
  transform: translateY(-4px);
  box-shadow: 0 6px 20px rgba(22, 160, 133, 0.5);
}

/* Applying the animation */
.animate-fade-in-slide-up {
  animation: fade-in-slide-up 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94) both;
  opacity: 0; /* Start as invisible */
}

/* Animation delays */
h1.animate-fade-in-slide-up {
  animation-delay: 0.5s; /* Delay for the heading */
}

.hero-button.animate-fade-in-slide-up {
  animation-delay: 1.2s; /* Delay for the button, appears after heading */
}


/* Responsive Styles */
@media (max-width: 768px) {
  .hero-content h1 {
    font-size: 2.5rem;
  }

  .typewriter-text {
    font-size: 1.5rem;
  }
  
  :deep(.Typewriter__cursor) {
    font-size: 1.5rem;
  }
}
</style>