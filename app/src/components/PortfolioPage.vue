<!--
  @component PortfolioPage
  @description A portfolio page component that displays projects in a responsive grid layout.
              Features a modal view for detailed project information and smooth transitions.
  @example
  ```vue
  <PortfolioPage />
  ```
-->
<template>
  <div class="portfolio-container">
    <h1 class="portfolio-title">My Portfolio</h1>
    <div class="portfolio-grid">
      <div v-for="(project, index) in projects" 
           :key="index" 
           class="portfolio-item"
      >
        <div class="portfolio-card">
          <img :src="project.image" :alt="project.title" class="portfolio-image">
          <div class="portfolio-content">
            <h3 class="portfolio-item-title">{{ project.title }}</h3>
            <p class="portfolio-description">{{ project.description }}</p>
            <div class="portfolio-tags">
              <span v-for="tag in project.tags" 
                    :key="tag" 
                    class="portfolio-tag"
              >
                {{ tag }}
              </span>
            </div>
            <div class="portfolio-links">
              <a v-if="project.demo" 
                 :href="project.demo" 
                 class="portfolio-link demo"
                 target="_blank"
                 rel="noopener noreferrer"
              >
                Live Demo
              </a>
              <button 
                @click="openModal(project)"
                class="portfolio-link readmore"
              >
                Read More
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>    <!-- Modal -->
    <Transition name="fade">
      <div v-if="selectedProject" class="modal-overlay" @click="closeModal">
        <Transition name="slide-up">
          <div class="modal-content" @click.stop>
            <button class="modal-close" @click="closeModal">&times;</button>
            <img 
              :src="selectedProject.image" 
              :alt="selectedProject.title" 
              class="modal-image"
            >
            <h2 class="modal-title">{{ selectedProject.title }}</h2>
            <div class="modal-tags">
              <span v-for="tag in selectedProject.tags" 
                    :key="tag" 
                    class="portfolio-tag"
              >
                {{ tag }}
              </span>
            </div>
            <p class="modal-description">{{ selectedProject.description }}</p>
            <div class="modal-details">
              <h3>Project Details</h3>
              <p>{{ selectedProject.longDescription || 'A detailed description of the project and its technical implementation.' }}</p>
              
              <h3>Technical Implementation</h3>
              <ul class="modal-tech-list">
                <li v-for="(detail, index) in selectedProject.technicalDetails" 
                    :key="index"
                >
                  {{ detail }}
                </li>
              </ul>
              
              <h3>Key Features</h3>
              <ul class="modal-features-list">
                <li v-for="(feature, index) in selectedProject.features" 
                    :key="index"
                >
                  {{ feature }}
                </li>
              </ul>
            </div>
            <div class="modal-footer">
              <a v-if="selectedProject.demo" 
                 :href="selectedProject.demo" 
                 class="portfolio-link demo"
                 target="_blank"
                 rel="noopener noreferrer"
              >
                View Live Demo
              </a>
            </div>
          </div>
        </Transition>
      </div>
    </Transition>
  </div>
</template>

<script setup>
import { ref } from 'vue'

/**
 * Reference to the currently selected project for the modal view
 * @type {import('vue').Ref<{
 *   title: string,
 *   description: string,
 *   longDescription?: string,
 *   image: string,
 *   tags: string[],
 *   demo?: string,
 *   github?: string,
 *   technicalDetails?: string[],
 *   features?: string[]
 * } | null>}
 */
const selectedProject = ref(null)

/**
 * Opens the modal with the selected project details
 * @param {Object} project - The project to display in the modal
 * @param {string} project.title - Project title
 * @param {string} project.description - Short project description
 * @param {string} [project.longDescription] - Detailed project description
 * @param {string} project.image - URL of the project image
 * @param {string[]} project.tags - Array of technology tags
 * @param {string} [project.demo] - Demo URL
 * @param {string} [project.github] - GitHub repository URL
 * @param {string[]} [project.technicalDetails] - Array of technical specifications
 * @param {string[]} [project.features] - Array of project features
 */
function openModal(project) {
  selectedProject.value = project
  document.body.style.overflow = 'hidden' // Prevent body scroll when modal is open
}

/**
 * Closes the modal and resets the selected project
 */
function closeModal() {
  selectedProject.value = null
  document.body.style.overflow = '' // Restore body scroll
}

/**
 * Portfolio projects data
 * @type {Array<{
 *   title: string,
 *   description: string,
 *   longDescription?: string,
 *   image: string,
 *   tags: string[],
 *   demo?: string,
 *   github?: string,
 *   technicalDetails?: string[],
 *   features?: string[]
 * }>}
 */
const projects = [
  {
    title: "Project 1",
    description: "Description of project 1. Add details about what the project does and the technologies used.",
    longDescription: "An in-depth look at Project 1. This project aimed to solve specific problems in the industry using cutting-edge technologies. The implementation involved careful consideration of user experience and performance optimization.",
    image: "https://picsum.photos/800/600?random=1",
    tags: ["Vue", "Python", "Machine Learning"],
    demo: "https://demo1.com",
    technicalDetails: [
      "Implemented using Vue 3 Composition API",
      "Python backend with FastAPI",
      "Machine Learning model trained on custom dataset",
      "Real-time data processing pipeline"
    ],
    features: [
      "Real-time data visualization",
      "Predictive analytics dashboard",
      "Custom reporting system",
      "Advanced filtering capabilities"
    ]
  },
  {
    title: "Project 2",
    description: "Description of project 2. Add details about what the project does and the technologies used.",
    image: "https://picsum.photos/800/600?random=2",
    tags: ["React", "Node.js", "MongoDB"],
    demo: "https://demo2.com",
    github: "https://github.com/username/project2"
  },
  {
    title: "Project 3",
    description: "Description of project 3. Add details about what the project does and the technologies used.",
    image: "https://picsum.photos/800/600?random=3",
    tags: ["Data Science", "Python", "TensorFlow"],
    demo: "https://demo3.com",
    github: "https://github.com/username/project3"
  },
{
    title: "Project 4",
    description: "Description of project 4. Add details about what the project does and the technologies used.",
    image: "https://picsum.photos/800/600?random=4",
    tags: ["Data Science", "Python", "TensorFlow"],
    demo: "https://demo3.com",
    github: "https://github.com/username/project3"
  }
  // Add more projects as needed
]
</script>

<style scoped>
.portfolio-container {
  padding: 2rem;
  max-width: 1400px;
  margin: 0 auto;
}

.portfolio-title {
  text-align: center;
  color: #22223b;
  font-size: 2.5rem;
  margin-bottom: 3rem;
  font-weight: 700;
}

.portfolio-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;
}

.portfolio-item {
  break-inside: avoid;
}

.portfolio-card {
  background: #ffffff;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 4px 20px rgba(124,93,250,0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.portfolio-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 30px rgba(124,93,250,0.15);
}

.portfolio-image {
  width: 100%;
  height: 200px;
  object-fit: cover;
}

.portfolio-content {
  padding: 1.5rem;
}

.portfolio-item-title {
  color: #22223b;
  font-size: 1.25rem;
  margin-bottom: 0.75rem;
  font-weight: 600;
}

.portfolio-description {
  color: #6b6b8d;
  font-size: 0.95rem;
  line-height: 1.5;
  margin-bottom: 1rem;
}

.portfolio-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1rem;
}

.portfolio-tag {
  background: #f3f0ff;
  color: #7c5dfa;
  padding: 0.3rem 0.8rem;
  border-radius: 20px;
  font-size: 0.85rem;
  font-weight: 500;
}

.portfolio-links {
  display: flex;
  gap: 1rem;
}

.portfolio-link {
  flex: 1;
  text-align: center;
  padding: 0.5rem 1rem;
  border-radius: 8px;
  font-size: 0.9rem;
  font-weight: 500;
  text-decoration: none;
  transition: background 0.3s ease, transform 0.3s ease;
}

.portfolio-link.demo {
  background: #7c5dfa;
  color: white;
}

.portfolio-link.demo:hover {
  background: #6c4ce0;
  transform: translateY(-2px);
}

.portfolio-link.readmore {
  background: #f3f0ff;
  color: #7c5dfa;
  border: none;
  cursor: pointer;
}

.portfolio-link.readmore:hover {
  background: #e6e0ff;
  transform: translateY(-2px);
}

/* 
 * Modal Styles
 * The modal system uses a combination of fixed positioning and flexbox
 * to create a centered, responsive modal with a blurred backdrop.
 * Includes smooth transitions for opening/closing animations.
 */
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
  padding: 2rem;
  backdrop-filter: blur(5px);
}

.modal-content {
  background: white;
  border-radius: 24px;
  padding: 2rem;
  max-width: 800px;
  width: 100%;
  max-height: 90vh;
  overflow-y: auto;
  position: relative;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
  scrollbar-width: none; /* Firefox */
  -ms-overflow-style: none; /* Internet Explorer/Edge */
}

.modal-content::-webkit-scrollbar {
  display: none; /* Chrome, Safari, Opera */
}

.modal-close {
  position: absolute;
  right: 1.5rem;
  top: 1.5rem;
  background: none;
  border: none;
  font-size: 2rem;
  color: #22223b;
  cursor: pointer;
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  transition: all 0.3s ease;
}

.modal-close:hover {
  background: #f3f0ff;
  color: #7c5dfa;
}

.modal-image {
  width: 100%;
  height: 300px;
  object-fit: cover;
  border-radius: 16px;
  margin-bottom: 1.5rem;
}

.modal-title {
  font-size: 2rem;
  color: #22223b;
  margin-bottom: 1rem;
}

.modal-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
}

.modal-description {
  color: #6b6b8d;
  font-size: 1.1rem;
  line-height: 1.6;
  margin-bottom: 2rem;
}

.modal-details {
  h3 {
    color: #22223b;
    font-size: 1.3rem;
    margin: 1.5rem 0 1rem 0;
  }

  p {
    color: #6b6b8d;
    line-height: 1.6;
    margin-bottom: 1.5rem;
  }
}

.modal-tech-list,
.modal-features-list {
  list-style: disc;
  padding-left: 1.5rem;
  margin-bottom: 1.5rem;
  color: #6b6b8d;
  
  li {
    margin-bottom: 0.5rem;
    line-height: 1.5;
  }
}

.modal-footer {
  margin-top: 2rem;
  display: flex;
  justify-content: center;
  gap: 1rem;
}

/* 
 * Transitions
 * Two transition types are used:
 * 1. Fade - For the modal overlay backdrop
 * 2. Slide-up - For the modal content entrance/exit
 */
/* Fade transition for overlay */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

/* Slide up transition for modal */
.slide-up-enter-active,
.slide-up-leave-active {
  transition: all 0.3s ease;
}

.slide-up-enter-from,
.slide-up-leave-to {
  transform: translateY(30px);
  opacity: 0;
}

/* 
 * Responsive Design Breakpoints
 * - 1200px: Switch from 3 columns to 2 columns
 * - 768px: Single column layout, adjusted spacing and font sizes
 */
@media (max-width: 1200px) {
  .portfolio-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 768px) {
  .portfolio-grid {
    grid-template-columns: 1fr;
  }
  
  .portfolio-container {
    padding: 1rem;
  }
  
  .portfolio-title {
    font-size: 2rem;
    margin-bottom: 2rem;
  }

  .modal-overlay {
    padding: 1rem;
  }

  .modal-content {
    padding: 1.5rem;
    border-radius: 16px;
  }

  .modal-title {
    font-size: 1.5rem;
  }

  .modal-image {
    height: 200px;
  }
}
</style>
