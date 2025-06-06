<template>
  <div class="tech-stack-wrapper">
    <div class="tech-stack-content">
      <h2 class="tech-stack-title">Tech Stack</h2>
      <div class="tech-grid">
        <div class="tech-item" v-for="(tech, index) in techStack" :key="index">
          <div class="tech-logo">
            <img :src="tech.logo" :alt="tech.name" />
          </div>
          <span class="tech-name">{{ tech.name }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const techStack = ref([
  {
    name: 'Python',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg'
  },
  {
    name: 'SQL',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mysql/mysql-original.svg'
  },
  {
    name: 'Rust',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/rust/rust-plain.svg'
  },
  {
    name: 'C++',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/cplusplus/cplusplus-original.svg'
  },
  {
    name: 'TensorFlow',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/tensorflow/tensorflow-original.svg'
  },
  {
    name: 'PyTorch',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/pytorch/pytorch-original.svg'
  },
  {
    name: 'Pandas',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/pandas/pandas-original.svg'
  },
  {
    name: 'Polars',
    logo: 'https://raw.githubusercontent.com/pola-rs/polars-static/master/logos/polars_github_logo_rect_dark_name.svg'
  },
  {
    name: 'NumPy',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/numpy/numpy-original.svg'
  },
  {
    name: 'Scikit-Learn',
    logo: 'https://upload.wikimedia.org/wikipedia/commons/0/05/Scikit_learn_logo_small.svg'
  },
  {
    name: 'Airflow',
    logo: 'https://cwiki.apache.org/confluence/download/attachments/145723561/airflow_64x64_emoji.png'
  },
  {
    name: 'Mage',
    logo: 'https://www.mage.ai/logo.png'
  },
  {
    name: 'Spark',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/apachespark/apachespark-original.svg'
  },
  {
    name: 'Kafka',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/apachekafka/apachekafka-original.svg'
  },
  {
    name: 'Docker',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original.svg'
  },
  {
    name: 'GCP',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/googlecloud/googlecloud-original.svg'
  },
  {
    name: 'AWS',
    logo: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/amazonwebservices/amazonwebservices-original.svg'
  },
  {
    name: 'Snowflake',
    logo: 'https://logos-world.net/wp-content/uploads/2022/11/Snowflake-Symbol.png'
  }
])
</script>

<style scoped>
.tech-stack-wrapper {
  width: 100vw;
  padding: 2rem;
  background: linear-gradient(135deg, #f8f6ff 0%, #f3f0ff 100%);
  box-sizing: border-box;
  display: flex;
  justify-content: center;
}

.tech-stack-content {
  width: 100%;
  max-width: 1000px;
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

.tech-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
  gap: 1.5rem;
  justify-items: center;
}

.tech-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 1.5rem 1rem;
  background: rgba(255, 255, 255, 0.6);
  border-radius: 16px;
  transition: all 0.3s ease;
  border: 1px solid rgba(124, 93, 250, 0.1);
  cursor: pointer;
  min-height: 120px;
  justify-content: center;
}

.tech-item:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 24px rgba(124, 93, 250, 0.15);
  background: rgba(255, 255, 255, 0.9);
  border-color: rgba(124, 93, 250, 0.3);
}

.tech-logo {
  width: 48px;
  height: 48px;
  margin-bottom: 0.8rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

.tech-logo img {
  width: 100%;
  height: 100%;
  object-fit: contain;
  filter: drop-shadow(0 2px 4px rgba(0, 0, 0, 0.1));
}

.tech-name {
  color: #22223b;
  font-size: 0.9rem;
  font-weight: 600;
  text-align: center;
  line-height: 1.2;
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

  .tech-grid {
    grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
    gap: 1.2rem;
  }

  .tech-item {
    padding: 1.2rem 0.8rem;
    min-height: 100px;
  }

  .tech-logo {
    width: 40px;
    height: 40px;
    margin-bottom: 0.6rem;
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

  .tech-grid {
    grid-template-columns: repeat(auto-fit, minmax(80px, 1fr));
    gap: 1rem;
  }
  
  .tech-item {
    padding: 1rem 0.5rem;
    min-height: 90px;
  }

  .tech-logo {
    width: 32px;
    height: 32px;
    margin-bottom: 0.5rem;
  }
  
  .tech-name {
    font-size: 0.8rem;
  }
}
</style>
