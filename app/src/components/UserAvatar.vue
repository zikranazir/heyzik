<template>
  <div class="avatar-container">
    <img :src="src" :alt="alt" class="avatar-img" />
  </div>
</template>

<script setup>
defineProps({
  src: {
    type: String,
    default: import.meta.env.BASE_URL + 'avatar.png'
  },
  alt: {
    type: String,
    default: 'Avatar'
  },
  size: {
    type: String,
    default: 'large' // large, medium, small
  }
})
</script>

<style scoped>
.avatar-container {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 1.5rem;
}

.avatar-img {
    border-radius: 50%;
    object-fit: cover;
    object-position: center 16%;
    box-shadow: 0 8px 32px rgba(124,93,250,0.13);
    border: 4px solid #fff;
    background: #f3f0ff;
    transition: transform 0.3s ease;
}

.avatar-img:hover {
  transform: scale(1.05);
}

/* Size variants */
.avatar-img {
  width: 200px;
  height: 200px;
}

@media (max-width: 900px) {
  .avatar-img {
    width: 100px;
    height: 100px;
  }
}
</style>
