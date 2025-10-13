<template>
  <section id="projects">
    <div class="projects-container">
      <h2 class="section-title">Proyek Saya</h2>
      <div class="projects-grid" ref="projectsGrid">
        <div v-for="(project, index) in projects" :key="project.id" class="project-card" :style="{ 'transition-delay': `${index * 150}ms` }">
          <img :src="project.image" :alt="project.title" class="project-image-bg">
          <div class="project-info-overlay">
            <div class="project-content">
              <h3 class="project-title">{{ project.title }}</h3>
              <p class="project-description">{{ project.description }}</p>
            </div>
            <div class="project-button-container">
              <a :href="project.link" class="project-button" target="_blank" rel="noopener noreferrer">Lihat</a>
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
  gap: 2.5rem;
}

.project-card {
  position: relative;
  height: 400px;
  border-radius: 15px;
  overflow: hidden;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
  text-align: left;
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.6s ease-out, transform 0.6s ease-out, box-shadow 0.4s ease;
}

.project-card.is-visible {
  opacity: 1;
  transform: translateY(0);
}

.project-card:hover {
  box-shadow: 0 15px 45px rgba(22, 160, 133, 0.35);
  transform: translateY(-10px) !important;
}

.project-image-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: 1;
  transition: transform 0.5s ease-out;
}

.project-card:hover .project-image-bg {
  transform: scale(1.1);
}

.project-info-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 2;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  padding: 1.5rem;
  padding-bottom: 2.5rem;
  color: white;
  background: linear-gradient(to top, rgba(0, 0, 0, 0.9) 20%, transparent 60%);
  transition: background 0.4s ease;
  box-sizing: border-box;
}

.project-card:hover .project-info-overlay {
  background: linear-gradient(to top, rgba(0, 0, 0, 1) 35%, transparent 70%);
}

.project-title {
  font-size: 1.8rem;
  font-weight: 700;
  color: white;
  margin-bottom: 0.5rem;
  line-height: 1.2;
  transform: translateY(80px);
  transition: transform 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

.project-card:hover .project-title {
  transform: translateY(0);
}

.project-description {
  font-size: 1rem;
  color: #e2e8f0;
  opacity: 0;
  max-height: 0;
  margin-bottom: 0;
  overflow: hidden;
  transition-property: opacity, max-height, margin-bottom;
  transition-duration: 0.4s;
  transition-timing-function: ease;
  /* HOVER-IN delay: Appears FIRST */
  transition-delay: 0.1s;
}

.project-card:hover .project-description {
  opacity: 1;
  max-height: 100px;
  margin-bottom: 1.25rem;
  /* HOVER-OUT delay: Disappears SECOND */
  transition-delay: 0.2s;
}

.project-button-container {
  opacity: 0;
  transform: translateY(15px);
  transition-property: opacity, transform;
  transition-duration: 0.4s;
  transition-timing-function: ease;
  /* HOVER-IN delay: Appears SECOND */
  transition-delay: 0s;
}

.project-card:hover .project-button-container {
  opacity: 1;
  transform: translateY(0);
  /* HOVER-OUT delay: Disappears FIRST */
  transition-delay: 0.2s;
}

.project-button {
  background-color: #16a085;
  color: white;
  padding: 0.75rem 1.75rem;
  border-radius: 50px;
  text-decoration: none;
  font-weight: 700;
  display: inline-block;
  box-shadow: 0 4px 15px rgba(0,0,0,0.2);
  transition: all 0.3s ease;
}

.project-button:hover {
  background-color: #19b698;
  transform: translateY(-2px) scale(1.03);
  box-shadow: 0 6px 20px rgba(22, 160, 133, 0.5);
}
</style>