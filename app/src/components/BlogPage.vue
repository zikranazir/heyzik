<template>
  <div class="blog-container">
    <h2 class="blog-title">Latest from Medium</h2>
    <div class="blog-grid">
      <article v-for="post in posts" 
               :key="post.guid" 
               class="blog-card"
               @click="openPost(post.link)"
      >
        <div class="blog-card-content">
          <p class="blog-date">{{ formatDate(post.pubDate) }}</p>
          <h3 class="blog-card-title">{{ post.title }}</h3>
          <p class="blog-excerpt" v-html="getExcerpt(post.description)"></p>
          <div class="blog-card-footer">
            <span class="read-more">Read More →</span>
          </div>
        </div>
      </article>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  posts: Array,
  formatDate: Function
})

function getExcerpt(html) {
  // Remove HTML tags and get plain text
  const text = html?.replace(/<[^>]+>/g, '') || ''
  // Get first 150 characters
  return text.slice(0, 150) + (text.length > 150 ? '...' : '')
}

function openPost(link) {
  window.open(link, '_blank', 'noopener')
}
</script>

<style scoped>
.blog-container {
  padding: 2rem;
  max-width: 900px;
  margin: 0 auto;
}

.blog-title {
  text-align: center;
  color: #22223b;
  font-size: 2.5rem;
  margin-bottom: 3rem;
  font-weight: 700;
}

.blog-grid {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.blog-card {
  background: #ffffff;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 4px 20px rgba(124,93,250,0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  cursor: pointer;
}

.blog-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 30px rgba(124,93,250,0.15);
}

.blog-card-content {
  padding: 2rem;
}

.blog-date {
  color: #7c5dfa;
  font-size: 0.9rem;
  font-weight: 500;
  margin-bottom: 0.5rem;
}

.blog-card-title {
  color: #22223b;
  font-size: 1.5rem;
  font-weight: 600;
  margin-bottom: 1rem;
  line-height: 1.3;
}

.blog-excerpt {
  color: #6b6b8d;
  font-size: 1rem;
  line-height: 1.6;
  margin-bottom: 1.5rem;
}

.blog-card-footer {
  display: flex;
  justify-content: flex-end;
  border-top: 1px solid #f0f0f0;
  padding-top: 1rem;
}

.read-more {
  color: #7c5dfa;
  font-weight: 600;
  font-size: 0.95rem;
  transition: transform 0.2s ease;
}

.blog-card:hover .read-more {
  transform: translateX(5px);
}

@media (max-width: 768px) {
  .blog-container {
    padding: 1rem;
  }

  .blog-title {
    font-size: 2rem;
    margin-bottom: 2rem;
  }

  .blog-card-content {
    padding: 1.5rem;
  }

  .blog-card-title {
    font-size: 1.25rem;
  }
}
</style>
