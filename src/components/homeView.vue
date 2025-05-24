<template>
  <div class="home">
    <div class="hero">
      <ProfileHeader />
      <div class="description">
        <p>Innovative Software Engineer with a strong foundation in programming and problem solving. I am
          enthusiastic about contributing to innovative projects and collaborating with cross-functional teams to
          solve complex business challenges. Committed to continuous learning and professional growth, I am
          excited about the opportunity to gain valuable skills, receive mentorship from industry professionals, and
          progress towards leadership roles within the organization.
        </p>
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