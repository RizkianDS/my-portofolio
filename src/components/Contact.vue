<template>
  <section id="contact">
    <div class="contact-container">
      <h2 class="section-title">Hubungi Saya</h2>
      <p class="contact-subtitle">Saya selalu terbuka untuk diskusi, kolaborasi, atau peluang baru. Jangan ragu untuk menghubungi saya!</p>
      <div class="contact-info">
        <a href="mailto:email@anda.com" class="contact-item">email@anda.com</a>
        <span class="separator">|</span>
        <a href="https://linkedin.com/in/namaanda" class="contact-item" target="_blank">LinkedIn</a>
        <span class="separator">|</span>
        <a href="https://github.com/namaanda" class="contact-item" target="_blank">GitHub</a>
      </div>
      <footer class="footer-text">
        <p>&copy; 2024 [Nama Anda]. Dibuat dengan Vue.js & Vite.</p>
      </footer>
    </div>
  </section>
</template>

<script setup>
// No script needed
</script>

<style>
#contact {
  background-color: #2d3748; /* Darker Gray */
  padding: 6rem 2rem;
  text-align: center;
}

.contact-container {
  /* max-width: 900px; */ /* Removed for full-width layout */
  margin: 0 auto;
  width: 100%;
  box-sizing: border-box;
}

.section-title {
  font-size: 2.5rem;
  font-weight: 700;
  color: white;
  margin-bottom: 1rem;
}

.contact-subtitle {
  font-size: 1.2rem;
  color: #a0aec0; /* Light Gray */
  margin-bottom: 3rem;
  /* max-width: 600px; */ /* Removed for full-width layout */
  margin-left: auto;
  margin-right: auto;
}

.contact-info {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  gap: 1rem;
  margin-bottom: 4rem;
}

.contact-item {
  color: #16a085; /* Teal */
  font-size: 1.1rem;
  font-weight: 500;
  text-decoration: none;
  transition: color 0.3s ease;
}

.contact-item:hover {
  color: #19b698; /* Lighter Teal */
}

.separator {
  color: #4a5568; /* Gray */
  font-size: 1.2rem;
}

.footer-text {
  color: #718096; /* Lighter Gray */
  font-size: 0.9rem;
}

@media (max-width: 768px) {
  .contact-info {
    flex-direction: column;
    gap: 1rem;
  }

  .separator {
    display: none; /* Hide separators on mobile */
  }
}
</style>
