<template>
  <div class="centered-landing">
    <nav class="centered-nav">
      <ul class="centered-nav-menu">
        <li>
          <a 
            href="#" 
            class="centered-nav-link" 
            :class="{ active: currentPage === 'home' }" 
            @click.prevent="setCurrentPage('home')"
          >
            Home
          </a>
        </li>
        <li>
          <a 
            href="#" 
            class="centered-nav-link" 
            :class="{ active: currentPage === 'portfolio' }" 
            @click.prevent="setCurrentPage('portfolio')"
          >
            Portfolio
          </a>
        </li>
        <li>
          <a 
            href="#" 
            class="centered-nav-link" 
            :class="{ active: currentPage === 'contact' }" 
            @click.prevent="setCurrentPage('contact')"
          >
            Contact
          </a>
        </li>
      </ul>
    </nav>
    
    <main class="centered-main">
      <HomePage v-if="currentPage === 'home'" />
      <PortfolioPage v-else-if="currentPage === 'portfolio'" />
      <ContactPage v-else-if="currentPage === 'contact'" />
    </main>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import HomePage from './components/HomePage.vue'
import PortfolioPage from './components/PortfolioPage.vue'
import ContactPage from './components/ContactPage.vue'

const currentPage = ref('home')

const setCurrentPage = (page) => {
  currentPage.value = page
}
</script>

<style>
/* Global styles */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Roboto', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  line-height: 1.6;
  color: #333;
  background: #ffffff;
  /* Hide scrollbar for webkit browsers */
  overflow-x: hidden;
}

/* Hide scrollbar for webkit browsers (Chrome, Safari, Edge) */
body::-webkit-scrollbar {
  display: none;
}

/* Hide scrollbar for Firefox */
html {
  scrollbar-width: none;
}

/* Hide scrollbar for IE and Edge */
body {
  -ms-overflow-style: none;
}

.centered-landing {
  min-height: 100vh;
  background: #ffffff;
}

.centered-nav {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.2);
  padding: 0.75rem 0;
}

.centered-nav-menu {
  display: flex;
  justify-content: center;
  list-style: none;
  gap: 1.5rem;
  max-width: 600px;
  margin: 0 auto;
  padding: 0 1rem;
}

.centered-nav-link {
  text-decoration: none;
  color: #6c7b95;
  font-weight: 500;
  padding: 0.5rem 1rem;
  border-radius: 8px;
  transition: all 0.3s ease;
  font-size: 0.95rem;
}

.centered-nav-link:hover,
.centered-nav-link.active {
  color: #0b610f;
  background: rgba(49, 47, 47, 0.1);
}

.centered-main {
  padding-top: 70px;
  min-height: 100vh;
}

/* Mobile-first responsive design */
@media (max-width: 768px) {
  .centered-nav {
    padding: 0.5rem 0;
  }
  
  .centered-nav-menu {
    gap: 0.5rem;
    padding: 0 0.5rem;
  }
  
  .centered-nav-link {
    padding: 0.4rem 0.6rem;
    font-size: 0.85rem;
  }
  
  .centered-main {
    padding-top: 60px;
  }
}

@media (max-width: 480px) {
  .centered-nav {
    padding: 0.4rem 0;
  }
  
  .centered-nav-menu {
    gap: 0.2rem;
    padding: 0 0.3rem;
  }
  
  .centered-nav-link {
    padding: 0.3rem 0.5rem;
    font-size: 0.8rem;
    border-radius: 6px;
  }
  
  .centered-main {
    padding-top: 55px;
  }
}

/* Very small screens */
@media (max-width: 320px) {
  .centered-nav-menu {
    gap: 0.1rem;
  }
  
  .centered-nav-link {
    padding: 0.25rem 0.4rem;
    font-size: 0.75rem;
  }
}
</style>
