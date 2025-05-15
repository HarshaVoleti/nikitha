<template>
  <div class="home">
    <div class="hero">
      <ProfileHeader />
      <div class="description">
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</p>
      </div>
    </div>
    <SkillsSection />
    <ProjectsSection />
    <ExperienceSection />
    <ContactSection />
  </div>
</template>

<script>
  import ProfileHeader from './ProfileHeader.vue'
  import ProjectsSection from './ProjectsSection.vue'
  import ExperienceSection from './ExperienceSection.vue';
  import SkillsSection from './SkillsSection.vue';
  import ContactSection from './ContactSection.vue';


export default {
  name: 'HomeView',
  components: {
    ProfileHeader,
    ProjectsSection,
    ExperienceSection,
    SkillsSection,
    ContactSection

  }
}
</script>

<style lang="scss" scoped>
.home {
  min-height: 100vh;
  padding: 2rem;
}

.hero {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.description {
  margin-top: 2rem;
  padding: 0 2rem;
  max-width: 800px;
  width: 100%;
  
  p {
    margin-bottom: 1.5rem;
    font-size: 1.1rem;
    line-height: 1.8;
    color: var(--text-light);
    
    .dark & {
      color: var(--text-dark);
    }
  }
}
</style>