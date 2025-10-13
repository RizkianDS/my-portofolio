<template>
  <div>
    <Header @scrollToSection="handleScrollTo" />
    <main>
      <Hero />
      <Profile />
      <Projects />
      <Contact />
    </main>
  </div>
</template>

<script setup>
import Header from './components/Header.vue';
import Hero from './components/Hero.vue';
import Profile from './components/Profile.vue';
import Projects from './components/Projects.vue';
import Contact from './components/Contact.vue';

// This function handles the smooth scrolling when the event is received from the Header
const handleScrollTo = (selector) => {
  const element = document.querySelector(selector);
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' });
  }
};
</script>

<style>
/* Global styles remain the same */
html {
  scroll-behavior: smooth;
}

body {
  font-family: 'Poppins', sans-serif;
  background-color: #1a202c; /* Dark Blue */
  color: #e2e8f0; /* Light Gray */
  margin: 0;
  padding: 0;
}

section {
  /* All sections except Hero will have this padding */
  padding: 4rem 2rem;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  section {
    padding: 3rem 1rem;
  }
}
</style>
