<template>
  <header :class="{ 'scrolled': isScrolled, 'mobile-menu-open': isMobileMenuOpen }">
    <nav>
      <div class="logo-container">
        <a href="#home" @click.prevent="handleLinkClick('#home')">
          <img src="/icon.png" alt="Logo" class="logo-img">
          <span class="logo-text">Portofolio</span>
        </a>
      </div>

      <!-- Hamburger Menu Button -->
      <button class="hamburger" @click="toggleMobileMenu" aria-label="Toggle menu">
        <span class="line"></span>
        <span class="line"></span>
        <span class="line"></span>
      </button>

      <!-- Navigation Links -->
      <ul class="nav-links">
        <li><a href="#home" @click.prevent="handleLinkClick('#home')">Home</a></li>
        <li><a href="#profile" @click.prevent="handleLinkClick('#profile')">Profil</a></li>
        <li><a href="#projects" @click.prevent="handleLinkClick('#projects')">Proyek</a></li>
        <li><a href="#contact" @click.prevent="handleLinkClick('#contact')">Kontak</a></li>
      </ul>
    </nav>
  </header>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount, defineEmits } from 'vue';

const emit = defineEmits(['scrollToSection']);

const isScrolled = ref(false);
const isMobileMenuOpen = ref(false);

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50;
};

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value;
};

const handleLinkClick = (selector) => {
  emit('scrollToSection', selector);
  // Close the mobile menu automatically when a link is clicked
  if (isMobileMenuOpen.value) {
    isMobileMenuOpen.value = false;
  }
};

onMounted(() => {
  window.addEventListener('scroll', handleScroll);
});

onBeforeUnmount(() => {
  window.removeEventListener('scroll', handleScroll);
});
</script>

<style>
/* --- Base Header Styles --- */
header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  padding: 1rem 2.5rem;
  z-index: 1000;
  transition: background-color 0.4s ease, backdrop-filter 0.4s ease;
  box-sizing: border-box;
}

header.scrolled {
  background-color: rgba(26, 32, 44, 0.85);
  backdrop-filter: blur(10px);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.25);
}

nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
}

/* --- Logo --- */
.logo-container a {
  display: flex;
  align-items: center;
  text-decoration: none;
  color: white;
}
.logo-img {
  height: 40px;
  margin-right: 0.75rem;
}
.logo-text {
  font-size: 1.5rem;
  font-weight: 700;
}

/* --- Desktop Navigation --- */
.nav-links {
  list-style: none;
  display: flex;
  gap: 2.5rem;
  margin: 0;
  padding: 0;
}

.nav-links a {
  text-decoration: none;
  color: #e2e8f0;
  font-weight: 500;
  position: relative;
  transition: color 0.3s ease;
}

.nav-links a::after {
  content: '';
  position: absolute;
  width: 0;
  height: 2px;
  bottom: -5px;
  left: 50%;
  transform: translateX(-50%);
  background-color: #16a085;
  transition: width 0.3s ease;
}

.nav-links a:hover {
  color: white;
}

.nav-links a:hover::after {
  width: 100%;
}

/* --- Hamburger Menu (Hidden on Desktop) --- */
.hamburger {
  display: none;
  background: transparent;
  border: none;
  cursor: pointer;
  padding: 0;
  z-index: 1100; /* Ensures it's clickable above other content */
}

.hamburger .line {
  display: block;
  width: 25px;
  height: 3px;
  background-color: white;
  margin: 5px 0;
  transition: all 0.3s ease-in-out;
}

/* --- Responsive Styles (Mobile View) --- */
@media (max-width: 768px) {
  /* Show hamburger, hide desktop nav links */
  .hamburger {
    display: block;
  }

  .nav-links {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 2rem;
    background-color: #1a202c;
    position: fixed;
    top: 0;
    left: 100%; /* Start off-screen */
    width: 100%;
    height: 100vh;
    transition: left 0.4s ease-in-out;
  }
  
  /* When mobile menu is open, slide it into view */
  header.mobile-menu-open .nav-links {
    left: 0;
  }
  
  .nav-links a {
    font-size: 1.5rem;
  }
  
  /* Animate Hamburger to an 'X' when menu is open */
  header.mobile-menu-open .hamburger .line:nth-child(1) {
    transform: rotate(45deg) translate(5px, 5px);
  }
  header.mobile-menu-open .hamburger .line:nth-child(2) {
    opacity: 0;
  }
  header.mobile-menu-open .hamburger .line:nth-child(3) {
    transform: rotate(-45deg) translate(7px, -6px);
  }
}
</style>
