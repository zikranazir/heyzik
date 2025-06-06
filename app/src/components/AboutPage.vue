<template>
  <div class="about-wrapper">
    <div class="about-content">
      <UserAvatar :src="avatarSrc" :alt="`${name} Avatar`" />
      <h1 class="name">{{ name }}</h1>
      <p class="subtitle">{{ subtitle }}</p>
      <div class="description">
        <p>{{ description1 }}</p>
        <p v-if="description2">{{ description2 }}</p>
      </div>
      <div class="buttons" v-if="showContactButton">
        <button class="contact-btn" @click="handleNavigate('#contact')">
          {{ contactButtonText }}
        </button>
      </div>
      <div class="social-links">
        <a v-for="social in socials" :key="social.name" :href="social.url" class="social-link" target="_blank" rel="noopener noreferrer">
          <i :class="social.icon"></i>
        </a>
      </div>
    </div>
  </div>
  
  <!-- Tech Stack as separate section -->
  <TechStack />
</template>

<script setup>
import UserAvatar from './UserAvatar.vue'
import TechStack from './TechStack.vue'

const emit = defineEmits(['navigate'])

const props = defineProps({
  name: String,
  subtitle: String,
  description1: String,
  description2: String,
  buttons: Array,
  socials: Array,
  avatarSrc: String,
  showContactButton: {
    type: Boolean,
    default: true
  },
  contactButtonText: {
    type: String,
    default: 'Get In Touch'
  }
})

function handleNavigate(href) {
  emit('navigate', href)
}
</script>

<style scoped>
.about-wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 90vh;
  width: 100vw;
  padding: 2rem;
  background: linear-gradient(135deg, #f8f6ff 0%, #f3f0ff 100%);
  box-sizing: border-box;
  position: relative;
}

.about-content {
  width: 100%;
  max-width: 600px;
  background: rgba(255, 255, 255, 0.8);
  backdrop-filter: blur(10px);
  border-radius: 32px;
  padding: 3rem 2.5rem;
  text-align: center;
  box-shadow: 
    0 8px 32px rgba(124,93,250,0.1),
    0 0 0 1px rgba(255, 255, 255, 0.2);
  border: 1px solid rgba(255, 255, 255, 0.3);
}

.name {
  color: #22223b;
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
  letter-spacing: -0.02em;
}

.subtitle {
  color: #6c7b95;
  font-size: 1.1rem;
  margin-bottom: 2rem;
  font-weight: 500;
}

.description {
  color: #4a5568;
  font-size: 1rem;
  line-height: 1.6;
  margin-bottom: 2.5rem;
  max-width: 500px;
  margin-left: auto;
  margin-right: auto;
}

.description p {
  margin-bottom: 1rem;
}

.description p:last-child {
  margin-bottom: 0;
}

.buttons {
  margin-bottom: 2rem;
}

.contact-btn {
  background: linear-gradient(135deg, #7c5dfa 0%, #9333ea 100%);
  color: white;
  border: none;
  padding: 1rem 2rem;
  border-radius: 50px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 4px 16px rgba(124, 93, 250, 0.3);
}

.contact-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(124, 93, 250, 0.4);
}

.social-links {
  display: flex;
  justify-content: center;
  gap: 1.5rem;
}

.social-link {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 48px;
  height: 48px;
  background: rgba(124, 93, 250, 0.1);
  border-radius: 12px;
  color: #7c5dfa;
  text-decoration: none;
  transition: all 0.3s ease;
  font-size: 1.2rem;
}

.social-link:hover {
  background: #7c5dfa;
  color: white;
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(124, 93, 250, 0.3);
}

@media (max-width: 900px) {
  .about-wrapper {
    padding: 1.5rem 1rem;
    min-height: 80vh;
  }
  
  .about-content {
    padding: 2rem 1.5rem;
    border-radius: 24px;
  }

  .name {
    font-size: 2.2rem;
  }

  .subtitle {
    font-size: 1rem;
  }

  .description {
    font-size: 0.95rem;
  }
}

@media (max-width: 600px) {
  .about-wrapper {
    padding: 1rem 0.5rem;
    min-height: auto;
  }
  
  .about-content {
    padding: 1.5rem 1rem;
    border-radius: 20px;
  }

  .name {
    font-size: 2rem;
  }
  
  .subtitle {
    font-size: 0.95rem;
    margin-bottom: 1.5rem;
  }
  
  .description {
    font-size: 0.9rem;
    margin-bottom: 2rem;
  }
  
  .contact-btn {
    padding: 0.8rem 1.5rem;
    font-size: 0.9rem;
  }
  
  .social-links {
    gap: 1rem;
  }
  
  .social-link {
    width: 44px;
    height: 44px;
    font-size: 1.1rem;
  }
}
</style>
