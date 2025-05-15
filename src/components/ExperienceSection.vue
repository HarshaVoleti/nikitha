<template>
  <div class="experience-section">
    <h2 class="section-title">Experience</h2>
    <div class="timeline">
      <div v-for="experience in experiences" :key="experience.id" class="timeline-item">
        <div class="timeline-dot"></div>
        <div class="timeline-content">
          <div class="timeline-header">
            <h3 class="company">{{ experience.company }}</h3>
            <span class="date">{{ experience.period }}</span>
          </div>
          <h4 class="position">{{ experience.position }}</h4>
          <ul class="responsibilities">
            <li v-for="(responsibility, index) in experience.responsibilities" 
                :key="index">{{ responsibility }}</li>
          </ul>
          <div class="skills">
            <span v-for="skill in experience.skills" 
                  :key="skill" 
                  class="skill-tag">{{ skill }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ExperienceSection',
  data() {
    return {
      experiences: [
        {
          id: 1,
          company: 'Tech Company One',
          position: 'Senior Frontend Developer',
          period: '2021 - Present',
          responsibilities: [
            'Led a team of 5 developers in building responsive web applications',
            'Implemented new features using Vue.js and improved performance by 40%',
            'Mentored junior developers and conducted code reviews'
          ],
          skills: ['Vue.js', 'JavaScript', 'SCSS', 'Git', 'Agile']
        },
        {
          id: 2,
          company: 'Digital Agency',
          position: 'Web Developer',
          period: '2019 - 2021',
          responsibilities: [
            'Developed and maintained client websites using modern technologies',
            'Collaborated with designers to implement pixel-perfect layouts',
            'Optimized website performance and SEO'
          ],
          skills: ['HTML5', 'CSS3', 'JavaScript', 'React', 'WordPress']
        },
        // Add more experiences as needed
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
.experience-section {
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

.timeline {
  position: relative;
  padding: 2rem 0;
  
  &::before {
    content: '';
    position: absolute;
    left: 0;
    top: 0;
    height: 100%;
    width: 2px;
    background: linear-gradient(to bottom, var(--primary-light), var(--accent-light));
    
    .dark & {
      background: linear-gradient(to bottom, var(--primary-dark), var(--accent-dark));
    }
    
    @media (min-width: 768px) {
      left: 50%;
      transform: translateX(-50%);
    }
  }
}

.timeline-item {
  position: relative;
  margin-bottom: 3rem;
  padding-left: 2rem;
  
  @media (min-width: 768px) {
    width: 50%;
    padding-left: 0;
    
    &:nth-child(odd) {
      left: 0;
      padding-right: 3rem;
      
      .timeline-content {
        text-align: right;
        
        .skills {
          justify-content: flex-end;
        }
      }
    }
    
    &:nth-child(even) {
      left: 50%;
      padding-left: 3rem;
    }
  }
}

.timeline-dot {
  position: absolute;
  left: -6px;
  top: 0;
  width: 16px;
  height: 16px;
  border-radius: 50%;
  background: var(--primary-light);
  border: 3px solid var(--background-light);
  
  .dark & {
    background: var(--primary-dark);
    border-color: var(--background-dark);
  }
  
  @media (min-width: 768px) {
    left: auto;
    right: -8px;
    
    .timeline-item:nth-child(even) & {
      right: auto;
      left: -8px;
    }
  }
}

.timeline-content {
  background: var(--background-light);
  padding: 1.5rem;
  border-radius: 15px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
  
  .dark & {
    background: var(--background-dark);
  }
}

.timeline-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 0.5rem;
}

.company {
  font-size: 1.4rem;
  color: var(--primary-light);
  margin: 0;
  
  .dark & {
    color: var(--primary-dark);
  }
}

.date {
  font-size: 0.9rem;
  color: var(--text-light);
  opacity: 0.8;
  
  .dark & {
    color: var(--text-dark);
  }
}

.position {
  font-size: 1.1rem;
  color: var(--text-light);
  margin-bottom: 1rem;
  
  .dark & {
    color: var(--text-dark);
  }
}

.responsibilities {
  list-style-type: none;
  padding: 0;
  margin: 0 0 1rem 0;
  
  li {
    position: relative;
    padding-left: 1.5rem;
    margin-bottom: 0.5rem;
    color: var(--text-light);
    
    .dark & {
      color: var(--text-dark);
    }
    
    &::before {
      content: '•';
      position: absolute;
      left: 0;
      color: var(--primary-light);
      
      .dark & {
        color: var(--primary-dark);
      }
    }
  }
}

.skills {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.skill-tag {
  padding: 0.3rem 0.8rem;
  background: var(--primary-light);
  color: white;
  border-radius: 15px;
  font-size: 0.9rem;
  
  .dark & {
    background: var(--primary-dark);
  }
}
</style>