<template>
  <div class="profile-section">
    <div class="profile-container">
      <div class="image-container">
        <img src="@/assets/logo.png" alt="Nikitha's Profile" class="profile-image">
      </div>
    </div>
    <div class="text-container">
      <h1 class="name">Nikitha <span class="highlight">Pulineni</span></h1>
      <p class="tagline">Software Developer</p>
      <p class="contact-info">Hyderabad | Phone: 9908068540 | Email: pulinaninikitha@gmail.com</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProfileHeader'
}
</script>

<style lang="scss" scoped>
.profile-section {
  display: flex;
  align-items: center;
  gap: 4rem;
  padding: 4rem 2rem;
  max-width: 1200px;
  margin: 0 auto;

  @media (max-width: 768px) {
    flex-direction: column;
    text-align: center;
    gap: 2rem;
  }
}

.profile-container {
  flex-shrink: 0;
}

.image-container {
  width: 300px;
  height: 300px;
  border-radius: 50%;
  padding: 8px;
  background: linear-gradient(45deg, var(--primary-light), var(--accent-light));
  animation: borderRotate 8s linear infinite;

  .dark & {
    background: linear-gradient(45deg, var(--accent-dark), var(--primary-dark));
  }

  @media (max-width: 768px) {
    width: 250px;
    height: 250px;
  }
}

.profile-image {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  object-fit: cover;
  border: 4px solid var(--background-light);

  .dark & {
    border-color: var(--background-dark);
  }
}

.text-container {
  flex-grow: 1;
}

.name {
  font-size: 4rem;
  font-weight: 700;
  margin-bottom: 1rem;
  background: linear-gradient(45deg, var(--primary-light), var(--accent-light));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  
  .dark & {
    background: linear-gradient(45deg, var(--accent-dark), var(--primary-dark));
    -webkit-background-clip: text;
  }

  @media (max-width: 768px) {
    font-size: 3rem;
  }
}

.highlight {
  color: var(--accent-light);
  .dark & {
    color: var(--accent-dark);
  }
}

.tagline {
  font-size: 1.5rem;
  color: var(--text-light);
  opacity: 0.9;

  .dark & {
    color: var(--text-dark);
  }
}

@keyframes borderRotate {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
</style>