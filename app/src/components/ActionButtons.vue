<template>
  <div class="action-buttons">
    <a 
      v-for="btn in buttons" 
      :key="btn.label" 
      :href="btn.href" 
      :class="['btn', btn.type || 'secondary']"
      :target="btn.external ? '_blank' : undefined"
      :rel="btn.external ? 'noopener noreferrer' : undefined"
      @click.prevent="handleClick(btn.href)"
    >
      {{ btn.label }}
    </a>
  </div>
</template>

<script setup>
const emit = defineEmits(['navigate'])

defineProps({
  buttons: {
    type: Array,
    default: () => []
  },
  showContactButton: {
    type: Boolean,
    default: true
  },
  contactButtonText: {
    type: String,
    default: 'Get In Touch'
  }
})

function handleClick(href) {
  if (href.startsWith('#')) {
    emit('navigate', href)
  }
}
</script>

<style scoped>
.action-buttons {
  display: flex;
  gap: 1.2rem;
  flex-wrap: wrap;
  justify-content: center;
  margin-bottom: 2rem;
}

.btn {
  padding: 0.9rem 2rem;
  border-radius: 30px;
  font-size: 1rem;
  font-weight: 600;
  text-decoration: none;
  border: none;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 4px 16px rgba(124,93,250,0.1);
  display: inline-flex;
  align-items: center;
  justify-content: center;
  min-width: 140px;
}

.btn.primary {
  background: linear-gradient(135deg, #7c5dfa 0%, #a3c4f3 100%);
  color: #fff;
}

.btn.primary:hover {
  background: linear-gradient(135deg, #6c4ce0 0%, #8fb3e8 100%);
  transform: translateY(-2px);
  box-shadow: 0 6px 24px rgba(124,93,250,0.2);
}

.btn.secondary {
  background: #fff;
  color: #7c5dfa;
  border: 2px solid #e0e0e0;
}

.btn.secondary:hover {
  background: #f3f0ff;
  border-color: #7c5dfa;
  transform: translateY(-2px);
  box-shadow: 0 6px 24px rgba(124,93,250,0.15);
}

@media (max-width: 900px) {
  .action-buttons {
    flex-direction: column;
    align-items: center;
    gap: 1rem;
  }
  
  .btn {
    width: 100%;
    max-width: 280px;
  }
}
</style>
