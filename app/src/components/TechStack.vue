<template>
  <div class="tech-stack-wrapper">
    <div class="tech-stack-content">
      <h2 class="tech-stack-title">Tech Stack</h2>
      <div class="tech-category" v-for="(category, index) in categories" :key="index">
        <h3 class="category-title">{{ category.name }}</h3>
        <div class="tech-items">
          <div class="tech-item" v-for="(tech, techIndex) in category.items" :key="techIndex">
            {{ tech }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  categories: {
    type: Array,
    default: () => []
  }
})
</script>

<style scoped>
.tech-stack-wrapper {
  width: 100vw;
padding: 0.05rem;
  background: linear-gradient(135deg, #f8f6ff 0%, #f3f0ff 100%);
  box-sizing: border-box;
  display: flex;
  justify-content: center;
}

.tech-stack-content {
  width: 100%;
  max-width: 800px;
  background: rgba(255, 255, 255, 0.8);
  backdrop-filter: blur(10px);
  border-radius: 32px;
  padding: 3rem 2.5rem;
  box-shadow: 
    0 8px 32px rgba(124,93,250,0.1),
    0 0 0 1px rgba(255, 255, 255, 0.2);
  border: 1px solid rgba(255, 255, 255, 0.3);
}

.tech-stack-title {
  color: #22223b;
  font-size: 2rem;
  font-weight: 700;
  margin-bottom: 2rem;
  text-align: center;
}

.tech-category {
  text-align: left;
}

.category-title {
  color: #22223b;
  font-size: 1.1rem;
  font-weight: 600;
  margin-bottom: 0.8rem;
}

.tech-items {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
}

.tech-item {
  background: #f3f0ff;
  color: #7c5dfa;
  padding: 0.5rem 1rem;
  border-radius: 20px;
  font-size: 0.9rem;
  font-weight: 500;
  transition: all 0.3s ease;
  border: 1px solid rgba(124, 93, 250, 0.1);
}

.tech-item:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(124, 93, 250, 0.1);
  background: #e6e0ff;
}

@media (max-width: 900px) {
  .tech-stack-wrapper {
    padding: 1.5rem 1rem;
  }
  
  .tech-stack-content {
    padding: 2rem 1.5rem;
    border-radius: 24px;
  }

  .tech-stack-title {
    font-size: 1.8rem;
    margin-bottom: 1.5rem;
  }
}

@media (max-width: 600px) {
  .tech-stack-wrapper {
    padding: 1rem 0.5rem;
  }
  
  .tech-stack-content {
    padding: 1.5rem 1rem;
    border-radius: 20px;
  }

  .tech-stack-title {
    font-size: 1.6rem;
  }
  
  .category-title {
    font-size: 1rem;
  }
  
  .tech-item {
    font-size: 0.85rem;
    padding: 0.4rem 0.8rem;
  }
}
</style>
