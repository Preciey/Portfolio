<template>
  <section id="home" class="relative min-h-screen flex items-center justify-center overflow-hidden">
    <!-- Animated Background -->
    <div class="absolute inset-0 bg-gradient-primary dark:bg-gradient-dark"></div>
    
    <!-- Particles Background -->
    <div class="particles-bg">
      <div v-for="i in 20" :key="i" 
           class="particle"
           :style="particleStyle(i)">
      </div>
    </div>

    <!-- Floating gradient orbs -->
    <div class="absolute top-20 left-10 w-72 h-72 bg-rose-gold/20 rounded-full blur-3xl animate-float"></div>
    <div class="absolute bottom-20 right-10 w-96 h-96 bg-pink-300/20 rounded-full blur-3xl animate-float" style="animation-delay: 2s;"></div>

    <!-- Content -->
    <div class="relative z-10 section-container text-center">
      <div class="max-w-4xl mx-auto space-y-8 animate-fade-in">
        <!-- Greeting -->
        <div class="inline-block">
          <p class="text-rose-gold font-handwriting text-2xl md:text-3xl mb-4">Hello, I'm</p>
        </div>

        <!-- Name -->
        <h1 class="font-display text-5xl md:text-7xl lg:text-8xl font-bold mb-6">
          <span class="text-gradient">Precedence Ratambani</span>
        </h1>

        <!-- Headline -->
        <h2 class="text-2xl md:text-3xl lg:text-4xl font-display text-gray-700 dark:text-gray-300 mb-6">
          I build scalable, human-centered web applications.
        </h2>

        <!-- Subtext with tech stack -->
        <div class="flex flex-wrap justify-center gap-3 mb-8">
          <span v-for="tech in techStack" :key="tech" 
                class="px-4 py-2 bg-white/80 dark:bg-dark-card/80 backdrop-blur-sm rounded-full text-sm font-semibold text-gray-700 dark:text-gray-300 shadow-md hover:shadow-lg hover:scale-105 transition-all">
            {{ tech }}
          </span>
        </div>

        <!-- CTA Buttons -->
        <div class="flex flex-col sm:flex-row gap-4 justify-center items-center mt-12">
          <a href="#projects" class="btn-primary inline-flex items-center gap-2">
            <span>View My Work</span>
            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"></path>
            </svg>
          </a>
          <a href="#contact" class="btn-secondary">
            Let's Connect
          </a>
        </div>

        <!-- Scroll Indicator -->
        <div class="absolute bottom-10 left-1/2 transform -translate-x-1/2 animate-bounce">
          <svg class="w-6 h-6 text-rose-gold" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"></path>
          </svg>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'HeroSection',
  data() {
    return {
      techStack: ['Junior Software Developer', 'Vue.js', 'Laravel', 'Tailwind CSS', 'SQL']
    }
  },
  methods: {
    particleStyle(index) {
      const size = Math.random() * 10 + 5;
      const top = Math.random() * 100;
      const left = Math.random() * 100;
      const delay = Math.random() * 5;
      const duration = Math.random() * 5 + 5;
      
      return {
        width: `${size}px`,
        height: `${size}px`,
        top: `${top}%`,
        left: `${left}%`,
        animationDelay: `${delay}s`,
        animationDuration: `${duration}s`
      };
    }
  }
}
</script>

<style scoped>
/* Additional component-specific styles if needed */
</style>

