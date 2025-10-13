<template>
  <section id="projects">
    <div class="projects-container">
      <h2 class="section-title">Proyek Saya</h2>
      <div class="projects-grid" ref="projectsGrid">
        <div v-for="(project, index) in projects" :key="project.id" class="project-card" :style="{ 'transition-delay': `${index * 150}ms` }">
          <div class="project-image-container">
            <img :src="project.image" :alt="project.title" class="project-image">
          </div>
          <div class="project-info">
            <div class="project-content">
              <h3 class="project-title">{{ project.title }}</h3>
              <p class="project-description">{{ project.description }}</p>
            </div>
            <div class="project-button-container">
              <a :href="project.link" class="project-button" target="_blank" rel="noopener noreferrer">Lihat Proyek</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const projectsGrid = ref(null);

const projects = ref([
  {
    id: 1,
    title: 'DOA 5',
    description: 'Website untuk mengumpulkan tugas dan materi selama masa pelatihan di BBPVP Semarang.',
    image: '/p1.png',
    link: 'https://sites.google.com/view/doa5rizkiands/home'
  },
  {
    id: 2,
    title: 'NAPUFARI Kitchen',
    description: 'Sebuah situs web yang menampilkan menu, layanan katering, dan informasi kontak, dibuat untuk mempromosikan bisnis kuliner.',
    image: '/p2.png',
    link: 'https://sites.google.com/view/napufari-kitchen/home'
  }
]);

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('is-visible');
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.1 });

  const cards = projectsGrid.value.querySelectorAll('.project-card');
  cards.forEach(card => {
    observer.observe(card);
  });
});
</script>

<style scoped>
#projects {
  background-color: transparent; /* Changed from #1a202c */
  padding: 6rem 2rem;
  overflow-x: hidden;
}

.projects-container {
  max-width: 1200px;
  margin: 0 auto;
  text-align: center;
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
  display: flex;
  flex-direction: column;
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.6s ease-out, transform 0.6s ease-out, box-shadow 0.3s ease;
}

.project-card.is-visible {
  opacity: 1;
  transform: translateY(0);
}

.project-card:hover {
  transform: translateY(-5px) !important;
  box-shadow: 0 12px 35px rgba(22, 160, 133, 0.2);
}

.project-image-container {
  width: 100%;
  height: 200px;
  overflow: hidden;
}

.project-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.4s ease;
}

.project-card:hover .project-image {
  transform: scale(1.05);
}

.project-info {
  padding: 1.5rem;
  display: flex;
  flex-direction: column;
  flex-grow: 1;
  justify-content: space-between;
}

.project-content {
  transition: transform 0.4s ease;
}

.project-title {
  font-size: 1.5rem;
  font-weight: 600;
  color: white;
  margin-bottom: 0.5rem; /* Reduced margin */
}

.project-description {
  font-size: 1rem;
  color: #a0aec0;
  opacity: 0;
  max-height: 0;
  margin-bottom: 0;
  overflow: hidden;
  transition: opacity 0.4s ease, max-height 0.4s ease, margin-bottom 0.4s ease;
}

.project-card:hover .project-content {
  transform: translateY(-10px); /* Adjust this value as needed */
}

.project-card:hover .project-description {
  opacity: 1;
  max-height: 150px; /* Adjust based on description length */
  margin-bottom: 1rem; /* Space between description and button */
}

.project-button-container {
  margin-top: 0; /* No need for margin-top anymore */
}

.project-button {
  background-color: #16a085;
  color: white;
  padding: 0.75rem 1.5rem;
  border-radius: 50px;
  text-decoration: none;
  font-size: 0.9rem;
  font-weight: 600;
  transition: background-color 0.3s ease, transform 0.3s ease;
  box-shadow: 0 4px 10px rgba(22, 160, 133, 0.3);
  display: inline-block;
}

.project-button:hover {
  background-color: #19b698;
  transform: translateY(-3px);
}
</style>
