<template>
  <div class="skills-section">
    <h2 class="section-title">Skills & Technologies</h2>
    <div class="skills-grid">
      <div v-for="skill in skills" :key="skill.name" class="skill-card">
        <img :src="skill.icon" :alt="skill.name" class="skill-icon">
        <span class="skill-name">{{ skill.name }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SkillsSection',
  data() {
    return {
      skills: [
        {
          name: 'Java',
          icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-original.svg'
        },
        {
          name: 'Python',
          icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg'
        },
        {
          name: 'PostgreSQL',
          icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/postgresql/postgresql-original.svg'
        },
        {
          name: 'HTML',
          icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg'
        },
        {
          name: 'CSS',
          icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg'
        },
        {
          name: 'JavaScript',
          icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg'
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
.skills-section {
  padding: 4rem 2rem;
  max-width: 1200px;
  margin: 0 auto;
}

.section-title {
  font-size: 2.5rem;
  margin-bottom: 3rem;
  text-align: center;
  color: var(--text-light);
  
  .dark & {
    color: var(--text-dark);
  }
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
  gap: 2rem;
  justify-items: center;
}

.skill-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 1.5rem;
  background: var(--background-light);
  border-radius: 15px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  
  &:hover {
    transform: translateY(-5px);
    box-shadow: 0 6px 20px rgba(0, 0, 0, 0.15);
  }
  
  .dark & {
    background: var(--background-dark);
  }
}

.skill-icon {
  width: 50px;
  height: 50px;
  margin-bottom: 1rem;
  transition: transform 0.3s ease;
  
  .skill-card:hover & {
    transform: scale(1.1);
  }
}

.skill-name {
  font-size: 1rem;
  font-weight: 500;
  color: var(--text-light);
  text-align: center;
  
  .dark & {
    color: var(--text-dark);
  }
}
</style>