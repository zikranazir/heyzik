<template>
  <div class="portfolio-page">
    <div class="portfolio-header">
      <h1 class="portfolio-title">Portfolio</h1>
    </div>
    
    <div class="portfolio-grid">
      <div 
        v-for="item in portfolioItems" 
        :key="item.title" 
        class="portfolio-item"
        @click="openModal(item)"
      >
        <h3 class="portfolio-item-title">{{ item.title }}</h3>
        <p class="portfolio-item-desc">{{ item.description }}</p>
        <div class="portfolio-tech">{{ item.technologies }}</div>
      </div>
    </div>
    
    <!-- Modal -->
    <div v-if="showModal" class="modal-overlay" @click="closeModal">
      <div class="modal-content" @click.stop>
        <button class="modal-close" @click="closeModal">&times;</button>
        <div class="modal-header">
          <h2 class="modal-title">{{ selectedItem?.title }}</h2>
          <div class="modal-tech">{{ selectedItem?.technologies }}</div>
        </div>
        <div class="modal-body">
          <p class="modal-description">{{ selectedItem?.description }}</p>
          <div class="modal-details">
            <h3>Project Details</h3>
            <ul>
              <li><strong>Technologies:</strong> {{ selectedItem?.technologies }}</li>
              <li><strong>Type:</strong> Data Analysis & Visualization</li>
              <li><strong>Status:</strong> Completed</li>
            </ul>
          </div>
          
          <!-- CTA Buttons -->
          <div class="modal-actions">
            <a 
              v-if="selectedItem?.github" 
              :href="selectedItem.github" 
              target="_blank" 
              class="cta-button cta-github"
            >
              <svg class="cta-icon" viewBox="0 0 24 24" fill="currentColor">
                <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
              </svg>
              View on GitHub
            </a>
            <a 
              v-if="selectedItem?.demo" 
              :href="selectedItem.demo" 
              target="_blank" 
              class="cta-button cta-demo"
            >
              <svg class="cta-icon" viewBox="0 0 24 24" fill="currentColor">
                <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"/>
              </svg>
              Live Demo
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import yaml from 'js-yaml'

const portfolioItems = ref([])
const showModal = ref(false)
const selectedItem = ref(null)

const openModal = (item) => {
  selectedItem.value = item
  showModal.value = true
  document.body.style.overflow = 'hidden' // Prevent background scrolling
}

const closeModal = () => {
  showModal.value = false
  selectedItem.value = null
  document.body.style.overflow = 'auto' // Restore scrolling
}

async function loadPortfolioData() {
  try {
    const response = await fetch('/src/data/portfolio.yaml')
    const yamlText = await response.text()
    const data = yaml.load(yamlText)
    portfolioItems.value = data.portfolio
  } catch (error) {
    console.error('Error loading portfolio data:', error)
    portfolioItems.value = []
  }
}

onMounted(async () => {
  await loadPortfolioData()
})
</script>

<style scoped>
.portfolio-page {
  height: calc(100vh - 70px);
  padding: 2rem 2rem;
  max-width: 1200px;
  margin: 0 auto;
  font-family: 'Poppins', sans-serif;
  overflow-y: auto;
}

.portfolio-header {
  text-align: center;
  margin-bottom: 3rem;
}

.portfolio-title {
  font-size: 2.8rem;
  font-weight: 700;
  color: #232323;
  margin-bottom: 0.8rem;
  letter-spacing: -0.01em;
}

.portfolio-subtitle {
  font-size: 1.1rem;
  color: #6c7b95;
  font-weight: 400;
}

.portfolio-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2rem;
}

.portfolio-item {
  background: #fafbfc;
  border: 1px solid #e1e5e9;
  border-radius: 12px;
  padding: 2rem;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  cursor: pointer;
}

.portfolio-item:hover {
  transform: translateY(-4px);
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.12);
}

.portfolio-item-title {
  font-size: 1.2rem;
  font-weight: 600;
  color: #232323;
  margin-bottom: 1rem;
}

.portfolio-item-desc {
  font-size: 1rem;
  color: #6c7b95;
  line-height: 1.6;
  margin-bottom: 1.2rem;
}

.portfolio-tech {
  font-size: 0.9rem;
  color: #7c5dfa;
  font-weight: 500;
}

/* Modal Styles */
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
  padding: 2rem;
}

.modal-content {
  background: white;
  border-radius: 16px;
  max-width: 600px;
  width: 100%;
  max-height: 80vh;
  overflow-y: auto;
  position: relative;
  animation: modalSlideIn 0.3s ease-out;
}

@keyframes modalSlideIn {
  from {
    opacity: 0;
    transform: translateY(-20px) scale(0.95);
  }
  to {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}

.modal-close {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: none;
  border: none;
  font-size: 2rem;
  color: #6c7b95;
  cursor: pointer;
  transition: color 0.2s ease;
  line-height: 1;
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
}

.modal-close:hover {
  color: #232323;
  background: #f5f5f5;
}

.modal-header {
  padding: 2rem 2rem 1rem 2rem;
  border-bottom: 1px solid #e1e5e9;
}

.modal-title {
  font-size: 1.8rem;
  font-weight: 700;
  color: #232323;
  margin-bottom: 0.5rem;
  padding-right: 3rem;
}

.modal-tech {
  font-size: 0.9rem;
  color: #7c5dfa;
  font-weight: 500;
}

.modal-body {
  padding: 2rem;
}

.modal-description {
  font-size: 1.1rem;
  color: #6c7b95;
  line-height: 1.6;
  margin-bottom: 2rem;
}

.modal-details h3 {
  font-size: 1.2rem;
  font-weight: 600;
  color: #232323;
  margin-bottom: 1rem;
}

.modal-details ul {
  list-style: none;
  padding: 0;
}

.modal-details li {
  padding: 0.5rem 0;
  color: #6c7b95;
  border-bottom: 1px solid #f5f5f5;
}

.modal-details li:last-child {
  border-bottom: none;
}

.modal-details strong {
  color: #232323;
}

.modal-actions {
  display: flex;
  gap: 1rem;
  margin-top: 2rem;
}

.cta-button {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.75rem 1.5rem;
  border-radius: 8px;
  text-decoration: none;
  font-weight: 500;
  font-size: 0.95rem;
  transition: all 0.2s ease;
  flex: 1;
  justify-content: center;
}

.cta-icon {
  width: 18px;
  height: 18px;
}

.cta-github {
  background: #232323;
  color: white;
}

.cta-github:hover {
  background: #333333;
  transform: translateY(-1px);
}

.cta-demo {
  background: #7c5dfa;
  color: white;
}

.cta-demo:hover {
  background: #6b4ce6;
  transform: translateY(-1px);
}

@media (max-width: 768px) {
  .portfolio-page {
    height: calc(100vh - 60px);
    padding: 2rem 1rem;
  }
  
  .portfolio-title {
    font-size: 2.2rem;
  }
  
  .portfolio-grid {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }
  
  .portfolio-item {
    padding: 1.5rem;
  }
  
  .modal-overlay {
    padding: 1rem;
  }
  
  .modal-header {
    padding: 1.5rem 1.5rem 1rem 1.5rem;
  }
  
  .modal-body {
    padding: 1.5rem;
  }
  
  .modal-title {
    font-size: 1.5rem;
    padding-right: 2.5rem;
  }
  
  .modal-close {
    top: 0.8rem;
    right: 0.8rem;
    width: 35px;
    height: 35px;
    font-size: 1.5rem;
  }
  
  .modal-actions {
    flex-direction: column;
    gap: 0.75rem;
  }
  
  .cta-button {
    padding: 0.875rem 1rem;
    font-size: 0.9rem;
  }
  
  .cta-icon {
    width: 16px;
    height: 16px;
  }
}
</style>
