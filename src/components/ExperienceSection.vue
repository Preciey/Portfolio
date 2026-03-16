<template>
  <section id="experience" class="section-container bg-rose-50/10 ">
    <div class="max-w-5xl mx-auto ">
      <!-- Section Title -->
      <h2 class="section-title text-4xl font-bold text-[#b76e79] text-center pt-12">
        Work Experience
      </h2>

      <!-- Timeline -->
      <div class="relative mt-12">
        <!-- Vertical Line -->
        <div class="absolute left-8 md:left-1/2 top-0 bottom-0 w-0.5 bg-gradient-to-b from-[#b76e79] to-pink-300 transform md:-translate-x-1/2"></div>

        <!-- Experience Items -->
        <div v-for="(exp, index) in experiences" :key="index" 
             class="relative mb-12 reveal"
             :style="{ animationDelay: `${index * 0.2}s` }">
          
          <div class="flex flex-col md:flex-row items-start md:items-center gap-8">
            <!-- Timeline Dot -->
            <div class="absolute left-8 md:left-1/2 w-2 h-2 bg-[#b76e79] rounded-full transform -translate-x-1/2 ring-4 ring-[#b76e79] z-10"></div>

            <!-- Content Card (alternating sides on desktop) -->
            <div :class="[
              'ml-20 md:ml-0 w-full p-6 rounded-md shadow-md bg-white',
              index % 2 === 0 ? 'md:w-5/12 md:pr-12 md:text-right' : 'md:w-5/12 md:ml-auto md:pl-12'
            ]">
              <div class="card group">
                <!-- Date Badge -->
                <div class="inline-block mb-4">
                  <span class="px-4 py-2 bg-rose-100 text-[#b76e79] rounded-full text-sm font-semibold">
                    {{ exp.period }}
                  </span>
                </div>

                <!-- Position -->
                <h3 class="font-display text-2xl font-bold text-gray-800 dark:text-gray-200 mb-2 group-hover:text-[#b76e79] transition-colors">
                  {{ exp.position }}
                </h3>

                <!-- Company -->
                <p class="text-lg font-semibold text-[#b76e79] mb-4">
                  {{ exp.company }}
                </p>

                <!-- Description -->
                <p class="text-gray-600 dark:text-gray-400 leading-relaxed mb-4">
                  {{ exp.description }}
                </p>

                <!-- Key Achievements -->
                <div class="mt-4">
                  <ul class="space-y-2">
                    <li v-for="achievement in exp.achievements" :key="achievement"
                        class="flex items-start gap-2 text-sm text-gray-600 dark:text-gray-400">
                      <svg class="w-5 h-5 text-[#b76e79] flex-shrink-0 mt-0.5" fill="currentColor" viewBox="0 0 20 20">
                        <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd"></path>
                      </svg>
                      <span>{{ achievement }}</span>
                    </li>
                  </ul>
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
  name: 'ExperienceSection',
  data() {
    return {
      experiences: [
        {
          position: 'Junior Software Developer',
          company: 'Clear Access',
          period: 'Mar 2025 – Present',
          description: 'Leading development of innovative web applications using Vue.js and Laravel. Collaborating with cross-functional teams to deliver high-quality software solutions.',
          achievements: [
            'Developed and deployed 5+ major features for the library management system',
            'Improved application performance by 40% through code optimization',
            'Mentored junior developers in Vue.js best practices'
          ]
        },
        {
          position: 'Software Developer Intern',
          company: 'Clear Access',
          period: 'Mar 2024 – Mar 2025',
          description: 'Gained hands-on experience in full-stack development, working on various projects including admin portals and e-commerce integrations.',
          achievements: [
            'Built responsive UI components using Vue.js and Tailwind CSS',
            'Implemented RESTful APIs with Laravel backend',
            'Collaborated in agile sprints and code reviews'
          ]
        }
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

