<template>
  <section id="about" class="section-container bg-white pb-12 ">
    <div class="max-w-6xl mx-auto">
      <!-- Section Title -->
      <h2 class="section-title text-4xl font-bold text-[#b76e79] text-center pt-12 mb-12">
        About Me
      </h2>

      <div class="grid md:grid-cols-2 gap-12 items-center">
        <!-- Profile Image Placeholder -->
        <div class="reveal">
          <div class="relative">
            <div class="w-full aspect-square bg-gradient-to-br from-[#b76e79]/20 to-pink-300/20 rounded-3xl flex items-center justify-center overflow-hidden shadow-2xl">
              <!-- Decorative elements -->
              <div class="absolute top-0 right-0 w-32 h-32 bg-[#b76e79]/30 rounded-full blur-3xl"></div>
              <div class="absolute bottom-0 left-0 w-40 h-40 bg-pink-300/30 rounded-full blur-3xl"></div>
              
              <!-- Placeholder for profile image -->
              <div class="relative z-10 text-center p-8">
                <svg class="w-48 h-48 mx-auto text-[#b76e79]/40" fill="currentColor" viewBox="0 0 24 24">
                  <path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"/>
                </svg>
                <p class="font-handwriting text-2xl text-[#b76e79] mt-4">Precedence</p>
              </div>
            </div>
          </div>
        </div>
        <!-- About Content -->
        <div class="space-y-6 reveal">
          <div class="prose prose-lg ">
            <p class="text-lg text-gray-700  leading-relaxed">
              I'm an <span class="font-semibold text-[#b76e79]">innovative software developer</span> passionate about creating functional, scalable, and visually refined digital experiences. I specialize in front-end and back-end development using <span class="font-semibold">Vue.js, Laravel, and SQL</span>.
            </p>
            <p class="text-lg text-gray-700  leading-relaxed">
              I love solving complex challenges, optimizing performance, and collaborating in agile teams to deliver exceptional user experiences.
            </p>
          </div>

          <!-- Beyond the Code -->
          <div class="mt-8 p-6 bg-gradient-to-br from-soft-pink to-beige  rounded-2xl shadow-lg">
            <h3 class="font-display text-2xl font-semibold mb-4 text-gray-800 ">
              Beyond the Code
            </h3>
            <div class="flex flex-wrap gap-3">
              <span v-for="interest in interests" :key="interest"
                    class="px-4 py-2 bg-white/70  backdrop-blur-sm rounded-full text-sm font-medium text-gray-700  hover:bg-[#b76e79] hover:text-white transition-all cursor-default">
                {{ interest }}
              </span>
            </div>
          </div>

          <!-- Personal Touch -->
          <div class="mt-6">
            <p class="font-handwriting text-3xl text-[#b76e79]">
              "Creating beautiful experiences, one line of code at a time."
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'AboutSection',
  data() {
    return {
      interests: [
        'UI Design',
        'Cloud Computing',
        'Data Engineering',
        'Creative Tech',
        'Web Performance',
        'User Experience'
      ]
    }
  },
  mounted() {
    this.observeElements();
  },
  methods: {
    observeElements() {
      const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            entry.target.classList.add('active');
          }
        });
      }, { threshold: 0.1 });

      document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
    }
  }
}
</script>

