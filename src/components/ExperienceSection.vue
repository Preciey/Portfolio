<template>
  <section id="experience" class="section-container bg-rose-50/10 py-16 md:py-24 px-6">

    <div class="max-w-5xl mx-auto">

      <!-- Section Title -->
      <h2 class="section-title text-3xl md:text-4xl font-bold text-[#b76e79] text-center">
        Work Experience
      </h2>

      <!-- Timeline -->
      <div class="relative mt-10 md:mt-12">

        <!-- Vertical Line -->
        <div class="absolute left-4 md:left-1/2 top-0 bottom-0 w-0.5 bg-gradient-to-b from-[#b76e79] to-pink-300 md:-translate-x-1/2"></div>

        <!-- Experience -->
        <div v-for="(exp, index) in experiences"
             :key="index"
             class="relative mb-10 md:mb-12 reveal"
             :style="{ animationDelay: `${index * 0.2}s` }">

          <div class="flex flex-col md:flex-row items-start md:items-center">

            <!-- Timeline Dot -->
            <div class="absolute left-4 md:left-1/2 w-3 h-3 bg-[#b76e79] rounded-full transform -translate-x-1/2 ring-4 ring-rose-100 z-10"></div>

            <!-- Card -->
            <div :class="[

              'ml-12 md:ml-0 w-full p-5 md:p-6 rounded-xl shadow-md bg-rose-50 transition-all hover:shadow-lg',

              index % 2 === 0
                ? 'md:w-5/12 md:pr-12 md:text-right'
                : 'md:w-5/12 md:ml-auto md:pl-12'

            ]">

              <div class="group">

                <!-- Date -->
                <div class="inline-block mb-3 md:mb-4">

                  <span class="px-3 py-1 md:px-4 md:py-2 bg-rose-100 text-[#b76e79] rounded-full text-xs md:text-sm font-semibold">
                    {{ exp.period }}
                  </span>

                </div>

                <!-- Position -->
                <h3 class="font-display text-xl md:text-2xl font-bold text-gray-800 mb-2 group-hover:text-[#b76e79] transition">

                  {{ exp.position }}

                </h3>

                <!-- Company -->
                <p class="text-base md:text-lg font-semibold text-[#b76e79] mb-3 md:mb-4">

                  {{ exp.company }}

                </p>

                <!-- Description -->
                <p class="text-sm md:text-base text-gray-600 leading-relaxed mb-3 md:mb-4">

                  {{ exp.description }}

                </p>

                <!-- Achievements -->
                <ul class="space-y-2">

                  <li v-for="achievement in exp.achievements"
                      :key="achievement"
                      class="flex items-start gap-2 text-xs md:text-sm text-gray-600">

                    <svg class="w-4 h-4 md:w-5 md:h-5 text-[#b76e79] flex-shrink-0 mt-0.5"
                         fill="currentColor"
                         viewBox="0 0 20 20">

                      <path fill-rule="evenodd"
                        d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z"
                        clip-rule="evenodd">
                      </path>

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

          description:
            'Leading development of innovative web applications using Vue.js and Laravel. Collaborating with cross-functional teams to deliver high-quality software solutions.',

          achievements: [
            'Developed and deployed 5+ major features',
            'Improved application performance by 40%',
            'Mentored junior developers in Vue.js'
          ]

        },

        {
          position: 'Software Developer Intern',
          company: 'Clear Access',
          period: 'Mar 2024 – Mar 2025',

          description:
            'Gained hands-on experience in full-stack development including admin portals and integrations.',

          achievements: [
            'Built responsive UI with Vue + Tailwind',
            'Implemented REST APIs in Laravel',
            'Worked in agile sprints'
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

      const observer = new IntersectionObserver((entries)=>{

        entries.forEach(entry=>{

          if(entry.isIntersecting){
            entry.target.classList.add('active');
          }

        });

      },{threshold:0.1});

      document
        .querySelectorAll('.reveal')
        .forEach(el=>observer.observe(el));

    }

  }

}
</script>