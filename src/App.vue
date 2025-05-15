<template>
  <div :class="['app', theme]">
    <nav class="nav">
      <button @click="toggleTheme" class="theme-toggle">
        <span v-if="theme === 'light'">🌙</span>
        <span v-else>☀️</span>
      </button>
    </nav>
    <router-view v-slot="{ Component }">
      <transition name="fade" mode="out-in">
        <component :is="Component" />
      </transition>
    </router-view>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      theme: 'light'
    }
  },
  methods: {
    toggleTheme() {
      this.theme = this.theme === 'light' ? 'dark' : 'light'
      document.body.setAttribute('data-theme', this.theme)
    }
  },
  mounted() {
    document.body.setAttribute('data-theme', this.theme)
  }
}
</script>

<style lang="scss">
:root {
  // Light theme colors
  --primary-light: #ffb4e6;
  --secondary-light: #e2c4ff;
  --accent-light: #b4f4e0;
  --text-light: #2c3e50;
  --background-light: #fff9fc;

  // Dark theme colors
  --primary-dark: #2d1b3d;
  --secondary-dark: #1a1b4b;
  --accent-dark: #ff6ec7;
  --text-dark: #ffffff;
  --background-dark: #13111c;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  transition: all 0.3s ease;
}

body {
  font-family: 'Poppins', sans-serif;
}

.app {
  min-height: 100vh;
  
  &.light {
    background-color: var(--background-light);
    color: var(--text-light);
  }
  
  &.dark {
    background-color: var(--background-dark);
    color: var(--text-dark);
  }
}

.nav {
  padding: 1rem 2rem;
  display: flex;
  justify-content:end;
  align-items: center;
  
  .theme-toggle {
    background: none;
    border: none;
    font-size: 1.5rem;
    cursor: pointer;
    padding: 0.5rem;
    border-radius: 50%;
    transition: transform 0.3s ease;
    
    &:hover {
      transform: rotate(45deg);
    }
  }
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>