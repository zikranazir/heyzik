<template>
  <div class="about-wrapper">
    <div class="about-content">
      <UserAvatar 
        :src="avatarSrc || '/avatar.png'" 
        :alt="name || 'Avatar'" 
      />
      
      <UserInfo 
        :name="name"
        :subtitle="subtitle"
        :description1="description1"
        :description2="description2"
      />
      
      <ActionButtons 
        :buttons="buttons"
        :show-contact-button="false"
        @navigate="handleNavigate"
      />
      
      <SocialLinks :socials="socials" />
    </div>
  </div>
</template>

<script setup>
import UserAvatar from './UserAvatar.vue'
import UserInfo from './UserInfo.vue'
import ActionButtons from './ActionButtons.vue'
import SocialLinks from './SocialLinks.vue'

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
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  max-width: 800px;
  width: 100%;
  background: rgba(255, 255, 255, 0.8);
  backdrop-filter: blur(10px);
  border-radius: 32px;
  padding: 3rem 2.5rem;
  box-shadow: 
    0 8px 32px rgba(124,93,250,0.1),
    0 0 0 1px rgba(255, 255, 255, 0.2);
  border: 1px solid rgba(255, 255, 255, 0.3);
  box-sizing: border-box;
}

@media (max-width: 900px) {
  .about-wrapper {
    min-height: 100%;
    padding: 1.5rem 1rem;
  }
  
  .about-content {
    padding: 2rem 1.5rem;
    border-radius: 24px;
  }
}

@media (max-width: 600px) {
  .about-wrapper {
    padding: 1rem 0.5rem;
  }
  
  .about-content {
    padding: 1.5rem 1rem;
    border-radius: 20px;
  }
}
</style>
