<template>
  <section id="contact">
    <div class="contact-container">
      <h2 class="section-title">Hubungi Saya</h2>
      <p class="contact-subtitle">Saya selalu terbuka untuk diskusi, kolaborasi, atau peluang baru. Jangan ragu untuk menghubungi saya!</p>

      <!-- Form Card -->
      <div class="form-card">
        <form @submit.prevent="handleFormSubmit" class="contact-form">
          <div class="form-group">
            <label for="email" class="form-label">Email Anda</label>
            <input id="email" type="email" v-model="form.email" placeholder="contoh@email.com" required class="form-input">
          </div>
          <div class="form-group">
            <label for="message" class="form-label">Pesan Anda</label>
            <textarea id="message" v-model="form.message" placeholder="Tuliskan pesan Anda di sini..." required class="form-textarea"></textarea>
          </div>
          <button type="submit" class="submit-btn">Kirim Pesan</button>
        </form>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';

const form = ref({
  email: '',
  message: ''
});

const handleFormSubmit = () => {
  const subject = '[Tawaran Pekerjaan]';
  const body = `${form.value.message}\n\n---\nEmail Pengirim: ${form.value.email}`;
  const mailtoLink = `mailto:rizkiands10@gmail.com?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(body)}`;
  window.location.href = mailtoLink;
};
</script>

<style scoped>
#contact {
  background-color: #2d3748;
  padding: 6rem 2rem 4rem; /* Adjusted padding to give space for the footer */
  text-align: center;
}

.contact-container {
  max-width: 700px;
  margin: 0 auto;
}

.section-title {
  color: white;
  font-size: 2.5rem;
  margin-bottom: 1rem;
}

.contact-subtitle {
  font-size: 1.2rem;
  color: #a0aec0;
  margin-bottom: 3rem;
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
}

/* Form Card */
.form-card {
  background-color: #1a202c;
  padding: 2.5rem;
  border-radius: 12px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
  margin-bottom: 3rem;
  text-align: left;
}

.contact-form {
  width: 100%;
}

.form-group {
  margin-bottom: 1.5rem;
}

.form-label {
  display: block;
  margin-bottom: 0.5rem;
  color: #e2e8f0;
  font-weight: 600;
}

.form-input,
.form-textarea {
  width: 100%;
  padding: 1rem;
  border: 2px solid #4a5568;
  background-color: #2d3748;
  color: #e2e8f0;
  border-radius: 8px;
  font-family: 'Poppins', sans-serif;
  font-size: 1rem;
  transition: border-color 0.3s ease, box-shadow 0.3s ease;
  box-sizing: border-box;
}

.form-input::placeholder,
.form-textarea::placeholder {
  color: #718096;
}

.form-input:focus,
.form-textarea:focus {
  outline: none;
  border-color: #16a085;
  box-shadow: 0 0 15px rgba(22, 160, 133, 0.5);
}

.form-textarea {
  min-height: 150px;
  resize: vertical;
}

.submit-btn {
  width: 100%;
  padding: 1rem 2rem;
  background-color: #16a085;
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 1.1rem;
  font-weight: 700;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.3s ease;
}

.submit-btn:hover {
  background-color: #117a65;
  transform: translateY(-2px);
}

@media (max-width: 768px) {
  #contact {
    padding: 4rem 1.5rem 3rem;
  }
  .form-card {
    padding: 2rem;
  }
}
</style>
