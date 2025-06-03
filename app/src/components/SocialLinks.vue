<template>
  <div class="social-links">
    <a 
      v-for="social in socials" 
      :key="social.title" 
      :href="social.href" 
      class="social-link" 
      :title="social.title" 
      target="_blank" 
      rel="noopener noreferrer"
    >
      <component :is="social.icon" />
    </a>
  </div>
</template>

<script setup>
defineProps({
  socials: {
    type: Array,
    default: () => []
  }
})
</script>

<style scoped>
.social-links {
  display: flex;
  gap: 1.5rem;
  flex-wrap: wrap;
  justify-content: center;
  margin-top: 1rem;
}

.social-link {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background: #f3f0ff;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #7c5dfa;
  transition: all 0.3s ease;
  font-size: 1.3rem;
  text-decoration: none;
  box-shadow: 0 4px 16px rgba(124,93,250,0.1);
}

.social-link:hover {
  background: #7c5dfa;
  color: #fff;
  transform: translateY(-3px);
  box-shadow: 0 8px 24px rgba(124,93,250,0.2);
}

@media (max-width: 900px) {
  .social-links {
    gap: 1.2rem;
  }
  
  .social-link {
    width: 45px;
    height: 45px;
    font-size: 1.2rem;
  }
}
</style>
