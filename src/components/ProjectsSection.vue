<template>
  <div class="projects-section">
    <h2 class="section-title">Projects</h2>
    <div class="projects-container">
      <div v-for="project in projects" :key="project.id" class="project-card" @click="showProjectDetails(project)">
        <img :src="project.image" :alt="project.title" class="project-image">
        <div class="project-info">
          <h3>{{ project.title }}</h3>
          <p>{{ project.description }}</p>
        </div>
        <div class="project-links" v-if="selectedProject === project">
          <button @click.stop="openLink(project.github)" class="btn github">
            <i class="fab fa-github"></i> GitHub
          </button>
          <button @click.stop="openLink(project.website)" class="btn website">
            <i class="fas fa-globe"></i> Website
          </button>
        </div>
      </div>
    </div>
    <div class="snackbar" :class="{ show: showSnackbar }">{{ snackbarMessage }}</div>
  </div>
</template>

<script>
export default {
  name: 'ProjectsSection',
  data() {
    return {
      selectedProject: null,
      showSnackbar: false,
      snackbarMessage: '',
      projects: [
        {
          id: 1,
          title: 'AI Enabled Music Recommendation System',
          description: 'Developed an AI-based music recommendation system using machine learning algorithms like cosine similarity for personalized music recommendations. Led a team of 3 members as Team Leader.',
          image: require('@/assets/logo.png'),
          github: '',
          website: ''
        },
        {
          id: 2,
          title: 'Portfolio Website',
          description: 'Designed and developed a portfolio website using HTML and CSS.',
          image: require('@/assets/logo.png'),
          github: '',
          website: ''
        }
      ]
    }
  },
  methods: {
    showProjectDetails(project) {
      this.selectedProject = this.selectedProject === project ? null : project
    },
    openLink(url) {
      if (!url) {
        this.showSnackbarMessage('Link not provided')
        return
      }
      window.open(url, '_blank')
    },
    showSnackbarMessage(message) {
      this.snackbarMessage = message
      this.showSnackbar = true
      setTimeout(() => {
        this.showSnackbar = false
      }, 3000)
    }
  }
}
</script>

<style lang="scss" scoped>
.projects-section {
  padding: 2rem;
  position: relative;
}

.section-title {
  font-size: 2.5rem;
  margin-bottom: 2rem;
  text-align: center;
  color: var(--text-light);
  
  .dark & {
    color: var(--text-dark);
  }
}

.projects-container {
  display: flex;
  overflow-x: auto;
  gap: 2rem;
  padding: 1rem;
  scroll-snap-type: x mandatory;
  -webkit-overflow-scrolling: touch;
  
  &::-webkit-scrollbar {
    height: 8px;
  }
  
  &::-webkit-scrollbar-track {
    background: var(--background-light);
    border-radius: 4px;
  }
  
  &::-webkit-scrollbar-thumb {
    background: var(--primary-light);
    border-radius: 4px;
  }
}

.project-card {
  flex: 0 0 300px;
  border-radius: 15px;
  overflow: hidden;
  background: var(--background-light);
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease;
  scroll-snap-align: start;
  cursor: pointer;
  position: relative;
  
  .dark & {
    background: var(--background-dark);
  }
  
  &:hover {
    transform: translateY(-5px);
  }
}

.project-image {
  width: 100%;
  height: 200px;
  object-fit: cover;
}

.project-info {
  padding: 1.5rem;
  
  h3 {
    font-size: 1.4rem;
    margin-bottom: 0.5rem;
    color: var(--text-light);
    
    .dark & {
      color: var(--text-dark);
    }
  }
  
  p {
    font-size: 1rem;
    color: var(--text-light);
    opacity: 0.8;
    
    .dark & {
      color: var(--text-dark);
    }
  }
}

.project-links {
  display: flex;
  gap: 1rem;
  padding: 1rem 1.5rem;
  background: rgba(255, 255, 255, 0.9);
  
  .dark & {
    background: rgba(0, 0, 0, 0.9);
  }
}

.btn {
  flex: 1;
  padding: 0.5rem;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-weight: 600;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  
  &.github {
    background: #24292e;
    color: white;
    
    &:hover {
      background: #1a1f24;
    }
  }
  
  &.website {
    background: var(--primary-light);
    color: white;
    
    &:hover {
      background: var(--primary-dark);
    }
  }
}

.snackbar {
  visibility: hidden;
  min-width: 250px;
  background-color: #333;
  color: #fff;
  text-align: center;
  border-radius: 2px;
  padding: 16px;
  position: fixed;
  z-index: 1;
  left: 50%;
  bottom: 30px;
  transform: translateX(-50%);
  
  &.show {
    visibility: visible;
    animation: fadein 0.5s, fadeout 0.5s 2.5s;
  }
}

@keyframes fadein {
  from { bottom: 0; opacity: 0; }
  to { bottom: 30px; opacity: 1; }
}

@keyframes fadeout {
  from { bottom: 30px; opacity: 1; }
  to { bottom: 0; opacity: 0; }
}
</style>