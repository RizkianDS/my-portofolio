<template>
  <section id="projects">
    <div class="projects-container">
      <h2 class="section-title">Proyek Saya</h2>
      <div class="projects-grid" ref="projectsGrid">
        <!-- Project Card 1 -->
        <div class="project-card">
          <img src="/bg.jpg" alt="Project 1" class="project-image">
          <div class="project-info">
            <h3 class="project-title">Nama Proyek 1</h3>
            <p class="project-description">Deskripsi singkat tentang proyek ini, teknologi yang digunakan, dan peran saya.</p>
            <a href="#" class="project-link" target="_blank">Lihat Proyek</a>
          </div>
        </div>
        <!-- Project Card 2 -->
        <div class="project-card">
          <img src="/bg.jpg" alt="Project 2" class="project-image">
          <div class="project-info">
            <h3 class="project-title">Nama Proyek 2</h3>
            <p class="project-description">Deskripsi singkat tentang proyek ini, teknologi yang digunakan, dan peran saya.</p>
            <a href="#" class="project-link" target="_blank">Lihat Proyek</a>
          </div>
        </div>
        <!-- Add more project cards as needed -->
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const projectsGrid = ref(null);

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('is-visible');
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.1 });

  // Observe each project card and apply a stagger delay
  const cards = projectsGrid.value.querySelectorAll('.project-card');
  cards.forEach((card, index) => {
    card.style.transitionDelay = `${index * 150}ms`;
    observer.observe(card);
  });
});
</script>

<style>
#projects {
  background-color: #1a202c;
  padding: 6rem 2rem;
  overflow-x: hidden; /* Prevent horizontal scrollbar issues during animation */
}

.projects-container {
  margin: 0 auto;
  text-align: center;
  width: 100%;
  box-sizing: border-box;
}

.section-title {
  font-size: 2.5rem;
  font-weight: 700;
  color: white;
  margin-bottom: 3rem;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

.project-card {
  background-color: #2d3748;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.2);
  text-align: left;
  
  /* Animation styles */
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.6s ease-out, transform 0.6s ease-out;
}

.project-card.is-visible {
  opacity: 1;
  transform: translateY(0);
}

.project-card:hover {
  transform: translateY(-5px) !important; /* Ensure hover is prioritized */
  box-shadow: 0 12px 35px rgba(0, 0, 0, 0.3);
  transition: transform 0.3s ease, box-shadow 0.3s ease; /* Faster transition for hover */
}

.project-image {
  width: 100%;
  height: 200px;
  object-fit: cover;
}

.project-info {
  padding: 1.5rem;
}

.project-title {
  font-size: 1.5rem;
  font-weight: 600;
  color: white;
  margin-bottom: 0.5rem;
}

.project-description {
  font-size: 1rem;
  color: #a0aec0;
  margin-bottom: 1.5rem;
}

.project-link {
  color: #16a085;
  text-decoration: none;
  font-weight: 600;
  transition: color 0.3s ease;
}

.project-link:hover {
  color: #19b698;
}
</style>
