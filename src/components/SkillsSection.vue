<template>
  <section id="skills" class="section-container ">
    <div class="max-w-6xl mx-auto">
      <!-- Section Title -->
      <h2 class="section-title text-4xl font-bold text-[#b76e79] text-center pt-12">
        Skills & Tools
      </h2>

      <!-- Skills Grid -->
      <div class="grid md:grid-cols-3 gap-8 mt-12 p-8 ">
        <!-- Frontend Skills -->
        <div class="card reveal group shadow-md rounded-md p-6 ">
          <div class="flex items-center gap-3 mb-6">
            <div class="w-12 h-12 bg-[#b76e79]/20 rounded-lg flex items-center justify-center group-hover:bg-[#b76e79] group-hover:scale-110 transition-all">
              <svg class="w-6 h-6 text-[#b76e79] group-hover:text-white transition-colors" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4"></path>
              </svg>
            </div>
            <h3 class="font-display text-2xl font-semibold text-gray-800">Frontend</h3>
          </div>
          <div class="space-y-3 ">
            <div v-for="skill in frontendSkills" :key="skill.name" class="skill-item">
              <div class="flex justify-between mb-2 ">
                <span class="font-medium text-gray-700 ">{{ skill.name }}</span>
                <span class="text-sm text-[#b76e79] font-semibold">{{ skill.level }}%</span>
              </div>
              <div class="w-full bg-gray-200  rounded-full h-2 overflow-hidden">
                <div class="bg-gradient-to-r from-[#b76e79] to-pink-400 h-full rounded-full transition-all duration-1000 ease-out skill-bar"
                     :style="{ width: skill.level + '%' }">
                </div>
              </div
            </div>
          </div>
        </div>

        <!-- Backend Skills -->
        <div class="card reveal group shadow-md rounded-md p-6" style="animation-delay: 0.1s;">
          <div class="flex items-center gap-3 mb-6">
            <div class="w-12 h-12 bg-[#b76e79]/20 rounded-lg flex items-center justify-center group-hover:bg-[#b76e79] group-hover:scale-110 transition-all">
              <svg class="w-6 h-6 text-[#b76e79] group-hover:text-white transition-colors" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 12h14M5 12a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v4a2 2 0 01-2 2M5 12a2 2 0 00-2 2v4a2 2 0 002 2h14a2 2 0 002-2v-4a2 2 0 00-2-2m-2-4h.01M17 16h.01"></path>
              </svg>
            </div>
            <h3 class="font-display text-2xl font-semibold text-gray-800 ">Backend</h3>
          </div>
          <div class="space-y-3">
            <div v-for="skill in backendSkills" :key="skill.name" class="skill-item">
              <div class="flex justify-between mb-2">
                <span class="font-medium text-gray-700 ">{{ skill.name }}</span>
                <span class="text-sm text-[#b76e79] font-semibold">{{ skill.level }}%</span>
              </div>
              <div class="w-full bg-gray-200  rounded-full h-2 overflow-hidden">
                <div class="bg-gradient-to-r from-[#b76e79] to-pink-400 h-full rounded-full transition-all duration-1000 ease-out skill-bar"
                     :style="{ width: skill.level + '%' }">
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Tools & Soft Skills -->
        <div class="card reveal group shadow-md rounded-md p-6" style="animation-delay: 0.2s;">
          <div class="flex items-center gap-3 mb-6">
            <div class="w-12 h-12 bg-[#b76e79]/20 rounded-lg flex items-center justify-center group-hover:bg-[#b76e79] group-hover:scale-110 transition-all">
              <svg class="w-6 h-6 text-[#b76e79] group-hover:text-white transition-colors" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z"></path>
              </svg>
            </div>
            <h3 class="font-display text-2xl font-semibold text-gray-800">Tools & More</h3>
          </div>
          <div class="space-y-4">
            <div>
              <h4 class="font-semibold text-gray-700  mb-3">Development Tools</h4>
              <div class="flex flex-wrap gap-2">
                <span v-for="tool in tools" :key="tool"
                      class="px-3 py-1 bg-[#b76e79]/10  text-[#b76e79] rounded-full text-sm font-medium hover:bg-[#b76e79] hover:text-white transition-all cursor-default">
                  {{ tool }}
                </span>
              </div>
            </div>
            <div class="mt-4">
              <h4 class="font-semibold text-gray-700  mb-3">Soft Skills</h4>
              <div class="space-y-2">
                <div v-for="skill in softSkills" :key="skill" 
                     class="flex items-center gap-2 text-gray-700 ">
                  <svg class="w-5 h-5 text-[#b76e79]" fill="currentColor" viewBox="0 0 20 20">
                    <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd"></path>
                  </svg>
                  <span class="text-sm">{{ skill }}</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  </section>
</template>

<script>
export default {
  name: 'SkillsSection',
  data() {
    return {
      frontendSkills: [
        { name: 'Vue.js', level: 85 },
        { name: 'JavaScript', level: 80 },
        { name: 'Tailwind CSS', level: 90 },
        { name: 'HTML5 & CSS3', level: 95 }
      ],
      backendSkills: [
        { name: 'Laravel', level: 80 },
        { name: 'PHP', level: 75 },
        { name: 'MySQL', level: 85 },
        { name: 'REST APIs', level: 80 }
      ],
      tools: ['Git', 'Oracle DB', 'VS Code', 'JSON'],
      softSkills: [
        'Analytical Thinking',
        'Team Collaboration',
        'Problem Solving',
        'Agile Methodology',
        'Communication'
      ]
    }
  },
  mounted() {
    this.observeElements();
    this.animateSkillBars();
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
    },
    animateSkillBars() {
      const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            const bars = entry.target.querySelectorAll('.skill-bar');
            bars.forEach(bar => {
              bar.style.width = bar.style.width; // Trigger animation
            });
          }
        });
      }, { threshold: 0.5 });

      document.querySelectorAll('.skill-item').forEach(el => observer.observe(el));
    }
  }
}
</script>

