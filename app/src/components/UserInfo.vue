<template>
  <div class="user-info">
    <h1 class="title">{{ name }}</h1>
    <p class="subtitle">{{ subtitle }}</p>
    <div class="description" v-if="description1 || description2">
      <p v-if="description1">{{ description1 }}</p>
      <p v-if="description2">{{ description2 }}</p>
    </div>
  </div>
</template>

<script setup>
defineProps({
  name: String,
  subtitle: String,
  description1: String,
  description2: String
})
</script>

<style scoped>
.user-info {
  text-align: center;
  margin-bottom: 2rem;
}

.title {
  font-size: 2.5rem;
  font-weight: 800;
  margin-bottom: 0.8rem;
  color: #22223b;
  line-height: 1.2;
}

.subtitle {
  font-size: 1.2rem;
  color: #7c7c9a;
  margin-bottom: 1.5rem;
  font-weight: 500;
}

.description {
  font-size: 1.1rem;
  color: #6b6b8d;
  line-height: 1.6;
  max-width: 600px;
  margin: 0 auto;
}

.description p {
  margin-bottom: 0.5rem;
}

.description p:last-child {
  margin-bottom: 0;
}

@media (max-width: 900px) {
  .title {
    font-size: 2rem;
  }
  
  .subtitle {
    font-size: 1.1rem;
  }
  
  .description {
    font-size: 1rem;
  }
}
</style>
