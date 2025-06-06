<template>
  <div class="centered-landing">
    <nav class="centered-nav">
      <ul class="centered-nav-menu">
        <li v-for="item in navItems" :key="item.label">
          <a :href="item.href" class="centered-nav-link" :class="{ active: activeNav === item.href }" @click.prevent="setActiveNav(item.href)">{{ item.label }}</a>
        </li>
      </ul>
    </nav>
    <main class="centered-main">
      <AboutPage v-if="activeNav === '#about'"
        :name="name"
        :subtitle="subtitle"
        :description1="description1"
        :description2="description2"
        :buttons="buttons"
        :socials="socials"
        :avatarSrc="avatarPath"
        @navigate="setActiveNav"
      />
      <PortfolioPage v-else-if="activeNav === '#portfolio'" />
      <BlogPage v-else-if="activeNav === '#blog'"
        :posts="mediumPosts"
        :formatDate="formatDate"
      />
      <ContactPage v-else-if="activeNav === '#contact'" />
    </main>
  </div>
</template>

<script setup>
import { ref, computed, onMounted } from 'vue'
import AboutPage from './components/AboutPage.vue'
import PortfolioPage from './components/PortfolioPage.vue'
import BlogPage from './components/BlogPage.vue'
import ContactPage from './components/ContactPage.vue'

const activeNav = ref('#about')
const avatarPath = computed(() => `${import.meta.env.BASE_URL}avatar.png`)

const name = ref('Zikra Wahyudi')
const subtitle = ref('(He/Him)')
const description1 = ref('A data wizard who transforms raw data into actionable insights, bringing together 4+ years of hands-on experience in data science and engineering')
const description2 = ref('')

const buttons = ref([
  { text: 'Get In Touch', href: '#contact', variant: 'primary' }
])

const socials = ref([
  { name: 'LinkedIn', icon: 'fab fa-linkedin', url: 'https://linkedin.com/in/your-profile' },
  { name: 'GitHub', icon: 'fab fa-github', url: 'https://github.com/your-username' },
  { name: 'Twitter', icon: 'fab fa-twitter', url: 'https://twitter.com/your-handle' },
  { name: 'Email', icon: 'fas fa-envelope', url: 'mailto:your.email@example.com' }
])

const navItems = ref([
  { label: 'About', href: '#about' },
  { label: 'Portfolio', href: '#portfolio' },
  { label: 'Blog', href: '#blog' },
  { label: 'Contact', href: '#contact' }
])

const mediumPosts = ref([])

function setActiveNav(href) {
  activeNav.value = href
}

function formatDate(dateString) {
  return new Date(dateString).toLocaleDateString('en-US', {
    year: 'numeric',
    month: 'long',
    day: 'numeric'
  })
}

onMounted(async () => {
  // Fetch Medium posts or other initialization
})
</script>

<style>
/* Global styles */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  line-height: 1.6;
  color: #333;
  background: #f8f6ff;
}

.centered-landing {
  min-height: 100vh;
  background: linear-gradient(135deg, #f8f6ff 0%, #f3f0ff 100%);
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
  padding: 1rem 0;
}

.centered-nav-menu {
  display: flex;
  justify-content: center;
  list-style: none;
  gap: 2rem;
  max-width: 600px;
  margin: 0 auto;
  padding: 0 2rem;
}

.centered-nav-link {
  text-decoration: none;
  color: #6c7b95;
  font-weight: 500;
  padding: 0.5rem 1rem;
  border-radius: 8px;
  transition: all 0.3s ease;
}

.centered-nav-link:hover,
.centered-nav-link.active {
  color: #7c5dfa;
  background: rgba(124, 93, 250, 0.1);
}

.centered-main {
  padding-top: 80px;
  min-height: 100vh;
}

@media (max-width: 600px) {
  .centered-nav-menu {
    gap: 1rem;
    padding: 0 1rem;
  }
  
  .centered-nav-link {
    padding: 0.4rem 0.8rem;
    font-size: 0.9rem;
  }
}
</style>
