<template>
  <section id="home" class="relative min-h-screen bg-rose-50 flex items-center justify-center overflow-hidden px-6">

    <!-- Animated Background -->
    <div class="absolute inset-0"></div>
    
    <!-- Particles -->
    <div class="particles-bg">
      <div v-for="i in 20"
           :key="i"
           class="particle"
           :style="particleStyle(i)">
      </div>
    </div>

    <!-- Floating orbs (hidden on small screens) -->
    <div class="hidden md:block absolute top-20 left-10 w-72 h-72 bg-[#b76e79]/20 rounded-full blur-3xl animate-float"></div>

    <div class="hidden md:block absolute bottom-20 right-10 w-96 h-96 bg-pink-300/20 rounded-full blur-3xl animate-float"
         style="animation-delay:2s;">
    </div>

    <!-- Content -->
    <div class="relative z-10 w-full max-w-5xl mx-auto text-center">

      <div class="space-y-6 md:space-y-8 animate-fade-in">

        <!-- Greeting -->
        <p class="text-[#b76e79] font-handwriting text-xl md:text-3xl">
          Hello, I'm
        </p>

        <!-- Name -->
        <h1 class="font-display text-4xl sm:text-5xl md:text-7xl lg:text-8xl font-bold text-[#b76e79] leading-tight">
          Precedence Ratambani
        </h1>

        <!-- Headline -->
        <h2 class="text-lg sm:text-xl md:text-3xl lg:text-4xl font-display text-gray-700 max-w-3xl mx-auto">
          I build scalable, human-centered web applications.
        </h2>

        <!-- Tech stack -->
        <div class="flex flex-wrap justify-center gap-2 md:gap-3 pt-4">

          <span v-for="tech in techStack"
                :key="tech"
                class="px-3 py-2 md:px-4 bg-white/80 rounded-full text-xs md:text-sm font-semibold text-gray-700 shadow-md hover:shadow-lg hover:scale-105 transition-all">

            {{ tech }}

          </span>

        </div>

        <!-- CTA -->
        <div class="flex flex-col sm:flex-row gap-4 justify-center items-center mt-10">

          <a href="#projects"
             class="w-full sm:w-auto border-2 border-[#b76e79] rounded-full py-3 px-8 bg-[#b76e79] text-white hover:bg-white hover:text-[#b76e79] transition-all">

            View My Work

          </a>

          <a href="#contact"
             class="w-full sm:w-auto border-2 border-[#b76e79] rounded-full py-3 px-8 text-[#b76e79] hover:bg-[#b76e79] hover:text-white transition-all">

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

      techStack: [
        'Javascript',
        'Vue.js',
        'Laravel',
        'Tailwind CSS',
        'SQL'
      ]

    }
  },

  methods: {

    particleStyle() {

      const size = Math.random() * 8 + 4;

      return {
        width: `${size}px`,
        height: `${size}px`,
        top: `${Math.random()*100}%`,
        left: `${Math.random()*100}%`,
        animationDelay: `${Math.random()*5}s`,
        animationDuration: `${Math.random()*6+6}s`
      }

    }

  }

}
</script>