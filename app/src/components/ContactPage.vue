<template>
  <div class="contact-container">
    <div class="contact-card">
      <h2 class="contact-title">Get In Touch</h2>
      <p class="contact-description">
        Feel free to reach out if you want to collaborate with me, or simply have a chat.
      </p>
      
      <form class="contact-form" @submit.prevent="handleSubmit">
        <div class="form-group">
          <label for="name">Name</label>
          <input 
            id="name"
            v-model="formData.name"
            type="text"
            required
            placeholder="Enter your name"
          />
        </div>

        <div class="form-group">
          <label for="email">Email</label>
          <input 
            id="email"
            v-model="formData.email"
            type="email"
            required
            placeholder="Enter your email"
          />
        </div>

        <div class="form-group">
          <label for="company">Company</label>
          <input 
            id="company"
            v-model="formData.company"
            type="text"
            placeholder="Enter your company name"
          />
        </div>

        <div class="form-group">
          <label for="message">Message</label>
          <textarea 
            id="message"
            v-model="formData.message"
            required
            rows="4"
            placeholder="What would you like to say?"
          ></textarea>
        </div>

        <button type="submit" class="submit-button" :disabled="isSubmitting">
          {{ isSubmitting ? 'Sending...' : 'Send Message' }}
        </button>
      </form>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'

const formData = reactive({
  name: '',
  email: '',
  company: '',
  message: ''
})

const isSubmitting = ref(false)

async function handleSubmit() {
  isSubmitting.value = true
  
  try {
    // Here you would typically send the form data to your backend
    console.log('Form submitted:', formData)
    
    // Simulate API call
    await new Promise(resolve => setTimeout(resolve, 1000))
    
    // Clear form
    formData.name = ''
    formData.email = ''
    formData.company = ''
    formData.message = ''
    
    alert('Message sent successfully!')
  } catch (error) {
    console.error('Error submitting form:', error)
    alert('Failed to send message. Please try again.')
  } finally {
    isSubmitting.value = false
  }
}
</script>

<style scoped>
.contact-container {
  padding: 1rem;
  max-width: 800px;
  margin: 0 auto;
}

.contact-card {
  background: rgba(255, 255, 255, 0.8);
  backdrop-filter: blur(10px);
  border-radius: 24px;
  padding: 3rem;
  box-shadow: 
    0 8px 32px rgba(124,93,250,0.1),
    0 0 0 1px rgba(255, 255, 255, 0.2);
  border: 1px solid rgba(255, 255, 255, 0.3);
}

.contact-title {
  text-align: center;
  color: #22223b;
  font-size: 2.5rem;
  margin-bottom: 1rem;
  font-weight: 700;
}

.contact-description {
  text-align: center;
  color: #6b6b8d;
  font-size: 1.1rem;
  margin-bottom: 2.5rem;
  line-height: 1.6;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.form-group label {
  color: #22223b;
  font-size: 0.95rem;
  font-weight: 500;
}

.form-group input,
.form-group textarea {
  padding: 0.8rem 1rem;
  border: 2px solid #e0e0e0;
  border-radius: 12px;
  font-size: 1rem;
  color: #22223b;
  background: #ffffff;
  transition: all 0.3s ease;
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: #7c5dfa;
  box-shadow: 0 0 0 4px rgba(124,93,250,0.1);
}

.form-group input::placeholder,
.form-group textarea::placeholder {
  color: #a0a0a0;
}

.submit-button {
  background: linear-gradient(135deg, #7c5dfa 0%, #a3c4f3 100%);
  color: white;
  border: none;
  padding: 1rem 2rem;
  border-radius: 12px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  margin-top: 1rem;
}

.submit-button:hover:not(:disabled) {
  background: linear-gradient(135deg, #6c4ce0 0%, #8fb3e8 100%);
  transform: translateY(-2px);
  box-shadow: 0 4px 20px rgba(124,93,250,0.2);
}

.submit-button:disabled {
  opacity: 0.7;
  cursor: not-allowed;
}

@media (max-width: 768px) {
  .contact-container {
    padding: 1rem;
  }

  .contact-card {
    padding: 2rem 1.5rem;
    border-radius: 20px;
  }

  .contact-title {
    font-size: 2rem;
  }

  .contact-description {
    font-size: 1rem;
    margin-bottom: 2rem;
  }
}
</style>
