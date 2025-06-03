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
import BlogPage from './components/BlogPage.vue'
import PortfolioPage from './components/PortfolioPage.vue'
import ContactPage from './components/ContactPage.vue'
import IconLinkedIn from './components/icons/IconCommunity.vue'
import IconGitHub from './components/icons/IconDocumentation.vue'
import IconTwitter from './components/icons/IconEcosystem.vue'
import IconMail from './components/icons/IconSupport.vue'

const avatarPath = computed(() => `${import.meta.env.BASE_URL}avatar.png`)

const name = ref('Zikra Wahyudi')
const subtitle = ref('(He/Him)')
const description1 = ref('A data wizard who transforms raw data into actionable insights, bringing together 4+ years of hands-on experience in data science and engineering')
const navItems = [
  { label: 'About', href: '#about' },
  { label: 'Portfolio', href: '#portfolio' },
  { label: 'Blog', href: '#blog' },
  { label: 'Contact', href: '#contact' }
]
const activeNav = ref('#about')
function setActiveNav(href) {
  activeNav.value = href
}
const buttons = [
  { label: 'Get In Touch', href: '#contact', type: 'primary' }
]
const socials = [
  { title: 'LinkedIn', href: '#', icon: IconLinkedIn },
  { title: 'GitHub', href: '#', icon: IconGitHub },
  { title: 'Twitter', href: '#', icon: IconTwitter },
  { title: 'Email', href: '#', icon: IconMail }
]

// --- Medium RSS Fetch ---
const mediumUsername = 'zikranazir' // TODO: change to your Medium username
const mediumPosts = ref([])
async function fetchMediumPosts() {
  // Use rss2json public API to convert RSS to JSON
  const url = `https://api.rss2json.com/v1/api.json?rss_url=https://medium.com/feed/@${mediumUsername}`
  try {
    const res = await fetch(url)
    const data = await res.json()
    if (data.status === 'ok') {
      mediumPosts.value = data.items.slice(0, 6) // show latest 6
    }
  } catch (e) {
    mediumPosts.value = []
  }
}
function formatDate(dateStr) {
  const d = new Date(dateStr)
  return d.toLocaleDateString()
}
onMounted(() => {
  fetchMediumPosts()
})
</script>

<style scoped>
.centered-landing {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  background: #faf8ff;
  margin: 0;
  padding: 0;
  width: 100vw;
  overflow-x: hidden;
}
.centered-nav {
  width: 100%;
  background: #fff;
  border-bottom: 1px solid #f0f0f0;
  margin: 0;
  padding: 0;
  position: sticky;
  top: 0;
  z-index: 100;
}
.centered-nav-menu {
  display: flex;
  justify-content: center;
  gap: 2.5rem;
  list-style: none;
  padding: 1.5rem 0 1rem 0;
  margin: 0;
}
.centered-nav-link {
  color: #22223b;
  text-decoration: none;
  font-size: 1.08rem;
  font-weight: 500;
  padding-bottom: 0.2rem;
  border-bottom: 2px solid transparent;
  transition: border 0.2s, color 0.2s;
}
.centered-nav-link.active, .centered-nav-link:hover {
  color: #7c5dfa;
  border-bottom: 2px solid #7c5dfa;
}
.centered-main {
  flex: 1;
  width: 100%;
  min-height: calc(100vh - 80px);
  margin: 0;
  padding: 0;
}
.centered-card {
  background: linear-gradient(135deg, #f8f6ff 60%, #f3f0ff 100%);
  border-radius: 24px;
  box-shadow: 0 4px 32px 0 rgba(124,93,250,0.07);
  padding: 3.5rem 2.5rem 2.5rem 2.5rem;
  max-width: 420px;
  width: 100%;
  text-align: center;
  position: relative;
  transition: max-width 0.2s;
}
.medium-list {
  list-style: none;
  padding: 0;
  margin: 0;
}
.medium-list-item {
  margin-bottom: 1.2rem;
  text-align: left;
}
.medium-link {
  color: #7c5dfa;
  font-weight: 600;
  text-decoration: none;
  font-size: 1.08rem;
}
.medium-link:hover {
  text-decoration: underline;
}
.medium-date {
  color: #aaa;
  font-size: 0.92rem;
  margin-left: 0.7rem;
}
.centered-avatar {
  width: 110px;
  height: 110px;
  border-radius: 50%;
  margin: 0 auto 2rem auto;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 2.5rem;
  color: #fff;
  font-weight: 700;
  box-shadow: 0 8px 32px rgba(124,93,250,0.13);
}
.centered-title {
  font-size: 2.7rem;
  font-weight: 800;
  margin-bottom: 0.7rem;
  color: #22223b;
}
.centered-subtitle {
  font-size: 1.25rem;
  color: #7c7c9a;
  margin-bottom: 1.5rem;
  font-weight: 500;
}
.centered-description {
  font-size: 1.1rem;
  color: #6b6b8d;
  margin-bottom: 2.2rem;
  line-height: 1.6;
}
.centered-buttons {
  display: flex;
  gap: 1.2rem;
  justify-content: center;
  margin-bottom: 2.2rem;
}
.centered-btn {
  padding: 0.9rem 2.1rem;
  border-radius: 30px;
  font-size: 1rem;
  font-weight: 600;
  text-decoration: none;
  border: none;
  cursor: pointer;
  transition: background 0.2s, color 0.2s, box-shadow 0.2s;
  box-shadow: 0 2px 8px rgba(124,93,250,0.07);
}
.centered-btn.primary {
  background: linear-gradient(135deg, #7c5dfa 60%, #a3c4f3 100%);
  color: #fff;
}
.centered-btn.primary:hover {
  background: #a3c4f3;
  color: #fff;
}
.centered-btn.secondary {
  background: #fff;
  color: #7c5dfa;
  border: 2px solid #e0e0e0;
}
.centered-btn.secondary:hover {
  background: #f3f0ff;
  color: #7c5dfa;
}
.centered-socials {
  display: flex;
  gap: 1.2rem;
  justify-content: center;
  margin-top: 1.5rem;
}
.centered-social {
  width: 44px;
  height: 44px;
  border-radius: 50%;
  background: #f3f0ff;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #7c5dfa;
  transition: background 0.2s, color 0.2s;
  font-size: 1.2rem;
}
.centered-social:hover {
  background: #7c5dfa;
  color: #fff;
}
@media (max-width: 600px) {
  .centered-card {
    padding: 2rem 0.7rem 1.5rem 0.7rem;
  }
  .centered-title {
    font-size: 2rem;
  }
  .centered-avatar {
    width: 70px;
    height: 70px;
    font-size: 1.5rem;
  }
}

/* Layout fixed for full viewport */
</style>
