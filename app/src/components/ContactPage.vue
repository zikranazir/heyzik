<template>
  <div class="contact-page">
    <div class="contact-header">
      <h1 class="contact-title">Contact</h1>
      <p class="contact-subtitle">Let's connect and collaborate</p>
    </div>
    
    <div class="contact-content">
      <div class="contact-form">
        <form @submit.prevent="handleSubmit">
          <div class="form-group">
            <label for="name">Name</label>
            <input type="text" id="name" v-model="form.name" required>
          </div>
          
          <div class="form-group">
            <label for="email">Email</label>
            <input type="email" id="email" v-model="form.email" required>
          </div>
          
          <div class="form-group">
            <label for="message">Message</label>
            <textarea id="message" v-model="form.message" rows="5" required></textarea>
          </div>
          
          <button type="submit" class="submit-btn">Send Message</button>
        </form>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const form = ref({
  name: '',
  email: '',
  message: ''
})

const handleSubmit = () => {
  // For now, just create a mailto link
  const subject = encodeURIComponent('Contact from Portfolio Website')
  const body = encodeURIComponent(`Name: ${form.value.name}\nEmail: ${form.value.email}\n\nMessage:\n${form.value.message}`)
  window.location.href = `mailto:zikranazir@protonmail.com?subject=${subject}&body=${body}`
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap');

.contact-page {
  height: calc(100vh - 70px);
  padding: 2rem 2rem;
  max-width: 1200px;
  margin: 0 auto;
  font-family: 'Poppins', sans-serif;
  overflow-y: auto;
}

.contact-header {
  text-align: center;
  margin-bottom: 3rem;
}

.contact-title {
  font-size: 2.8rem;
  font-weight: 700;
  color: #232323;
  margin-bottom: 0.8rem;
  letter-spacing: -0.01em;
}

.contact-subtitle {
  font-size: 1.1rem;
  color: #6c7b95;
  font-weight: 400;
}

.contact-content {
  max-width: 600px;
  margin: 0 auto;
}

.contact-form h2 {
  font-size: 1.8rem;
  font-weight: 600;
  color: #232323;
  margin-bottom: 1.5rem;
  text-align: center;
}

.form-group {
  margin-bottom: 1.5rem;
}

.form-group label {
  display: block;
  font-weight: 500;
  color: #232323;
  margin-bottom: 0.5rem;
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 0.75rem;
  border: 1px solid #e1e5e9;
  border-radius: 6px;
  font-family: inherit;
  font-size: 1rem;
  transition: border-color 0.2s;
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: #7c5dfa;
}

.submit-btn {
  background: #000000;
  color: white;
  border: none;
  padding: 0.875rem 2rem;
  border-radius: 6px;
  font-family: inherit;
  font-size: 1rem;
  font-weight: 500;
  cursor: pointer;
  transition: background-color 0.2s;
}

.submit-btn:hover {
  background: #0b610f;
}

@media (max-width: 768px) {
  .contact-page {
    height: calc(100vh - 60px);
    padding: 2rem 1rem;
  }
  
  .contact-title {
    font-size: 2.2rem;
  }
  
  .contact-form h2 {
    font-size: 1.6rem;
  }
}
</style>