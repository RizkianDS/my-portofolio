<template>
  <div>
    <Header @scrollToSection="handleScrollTo" />
    <main>
      <Hero @scrollToSection="handleScrollTo" />
      <Profile />
      <Projects />
      <Contact />
    </main>
    <Footer />
  </div>
</template>

<script setup>
import Header from './components/Header.vue';
import Hero from './components/Hero.vue';
import Profile from './components/Profile.vue';
import Projects from './components/Projects.vue';
import Contact from './components/Contact.vue';
import Footer from './components/Footer.vue';

// Custom smooth scroll function remains the same
const easeInOutQuad = (t, b, c, d) => {
  t /= d / 2;
  if (t < 1) return c / 2 * t * t + b;
  t--;
  return -c / 2 * (t * (t - 2) - 1) + b;
};

const customSmoothScroll = (targetPosition, duration) => {
  const startPosition = window.pageYOffset;
  const distance = targetPosition - startPosition;
  let startTime = null;

  const animation = (currentTime) => {
    if (startTime === null) startTime = currentTime;
    const timeElapsed = currentTime - startTime;
    const run = easeInOutQuad(timeElapsed, startPosition, distance, duration);
    window.scrollTo(0, run);
    if (timeElapsed < duration) requestAnimationFrame(animation);
  };

  requestAnimationFrame(animation);
};

const handleScrollTo = (selector) => {
  const element = document.querySelector(selector);
  if (element) {
    const top = element.getBoundingClientRect().top + window.pageYOffset;
    customSmoothScroll(top, 1500);
  }
};
</script>

<style>
/*
  All global base styles (body, font, color, background) have been moved to src/style.css.
  This file now only contains layout rules for the main app structure.
*/

main {
  display: block; /* This is the natural behavior, but good to be explicit */
  margin: 0;
  padding: 0;
}

/* 
  This provides consistent padding for all content sections.
  The Hero component uses a <div> instead of a <section> 
  so it is not affected by this rule, allowing it to be full-width.
*/
section {
  padding: 4rem 2rem;
  box-sizing: border-box; 
}

/* Responsive adjustments for smaller screens */
@media (max-width: 768px) {
  section {
    padding: 3rem 1rem;
  }
}
</style>
