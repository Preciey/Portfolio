<template>
  <section id="home" class="relative min-h-screen bg-rose-50 flex items-center justify-center overflow-hidden">
    <!-- Animated Background -->
    <div class="absolute inset-0 "></div>
    
    <!-- Particles Background -->
    <div class="particles-bg">
      <div v-for="i in 20" :key="i" 
           class="particle"
           :style="particleStyle(i)">
      </div>
    </div>

    <!-- Floating gradient orbs -->
    <div class="absolute top-20 left-10 w-72 h-72 bg-[#b76e79]/20 rounded-full blur-3xl animate-float"></div>
    <div class="absolute bottom-20 right-10 w-96 h-96 bg-pink-300/20 rounded-full blur-3xl animate-float" style="animation-delay: 2s;"></div>

    <!-- Content -->
    <div class="relative z-10 section-container text-center">
      <div class="max-w-4xl mx-auto space-y-8 animate-fade-in">
        <!-- Greeting -->
        <div class="inline-block">
          <p class="text-[#b76e79] font-handwriting text-2xl md:text-3xl mb-4">Hello, I'm</p>
        </div>

        <!-- Name -->
        <h1 class="font-display text-5xl md:text-7xl lg:text-8xl font-bold mb-6 text-[#b76e79]">
          Precedence Ratambani
        </h1>

        <!-- Headline -->
        <h2 class="text-2xl md:text-3xl lg:text-4xl font-display text-gray-700 mb-6">
          I build scalable, human-centered web applications.
        </h2>

        <!-- Subtext with tech stack -->
        <div class="flex flex-wrap justify-center gap-3 mb-8">
          <span v-for="tech in techStack" :key="tech" 
                class="px-4 py-2 bg-white/80 rounded-full text-sm font-semibold text-gray-700 shadow-md hover:shadow-lg hover:scale-105 transition-all">
            {{ tech }}
          </span>
        </div>

        <!-- CTA Buttons -->
        <div class="flex flex-col flex-row gap-4 justify-center items-center mt-12">
          <a href="#projects" class="border-2 border-[#b76e79] rounded-full py-2 px-6 bg-[#b76e79] text-white hover:bg-white hover:text-[#b76e79] hover:ease-in transition-all">
            <span>View My Work</span>
          </a>
          <a href="#contact" class="border-2 rounded-full py-2 px-6 hover:border-[#b76e79] hover:bg-[#b76e79] text-[#b76e79] hover:text-white transition-all">
            Let's Connect
          </a>
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
      techStack: ['Javascript', 'Vue.js', 'Laravel', 'Tailwind CSS', 'SQL']
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

