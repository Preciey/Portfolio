<template>
  <section id="education" class="section-container bg-white dark:bg-dark-bg">
    <div class="max-w-5xl mx-auto">
      <!-- Section Title -->
      <h2 class="section-title reveal">
        <span class="text-gradient">Education</span>
      </h2>

      <!-- Education Grid -->
      <div class="grid md:grid-cols-3 gap-6 mt-12">
        <div v-for="(edu, index) in education" :key="index"
             class="card reveal group relative overflow-hidden"
             :style="{ animationDelay: `${index * 0.1}s` }">
          
          <!-- Decorative Corner -->
          <div class="absolute top-0 right-0 w-20 h-20 bg-rose-gold/10 rounded-bl-full group-hover:scale-150 transition-transform duration-500"></div>

          <!-- Icon -->
          <div class="relative mb-6">
            <div class="w-16 h-16 bg-gradient-to-br from-rose-gold to-pink-400 rounded-2xl flex items-center justify-center group-hover:scale-110 group-hover:rotate-6 transition-all duration-300 shadow-lg">
              <svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 14l9-5-9-5-9 5 9 5z"></path>
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 14l6.16-3.422a12.083 12.083 0 01.665 6.479A11.952 11.952 0 0012 20.055a11.952 11.952 0 00-6.824-2.998 12.078 12.078 0 01.665-6.479L12 14z"></path>
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 14l9-5-9-5-9 5 9 5zm0 0l6.16-3.422a12.083 12.083 0 01.665 6.479A11.952 11.952 0 0012 20.055a11.952 11.952 0 00-6.824-2.998 12.078 12.078 0 01.665-6.479L12 14zm-4 6v-7.5l4-2.222"></path>
              </svg>
            </div>
          </div>

          <!-- Degree -->
          <h3 class="font-display text-xl font-bold text-gray-800 dark:text-gray-200 mb-2 group-hover:text-rose-gold transition-colors">
            {{ edu.degree }}
          </h3>

          <!-- Institution -->
          <p class="text-rose-gold font-semibold mb-2">
            {{ edu.institution }}
          </p>

          <!-- Period -->
          <p class="text-sm text-gray-600 dark:text-gray-400 mb-4">
            {{ edu.period }}
          </p>

          <!-- Status Badge -->
          <div class="inline-block">
            <span :class="[
              'px-3 py-1 rounded-full text-xs font-semibold',
              edu.status === 'In Progress' 
                ? 'bg-green-100 text-green-700 dark:bg-green-900/30 dark:text-green-400'
                : 'bg-blue-100 text-blue-700 dark:bg-blue-900/30 dark:text-blue-400'
            ]">
              {{ edu.status }}
            </span>
          </div>

          <!-- Highlights -->
          <div v-if="edu.highlights" class="mt-4 pt-4 border-t border-gray-200 dark:border-gray-700">
            <ul class="space-y-2">
              <li v-for="highlight in edu.highlights" :key="highlight"
                  class="flex items-start gap-2 text-sm text-gray-600 dark:text-gray-400">
                <svg class="w-4 h-4 text-rose-gold flex-shrink-0 mt-0.5" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"></path>
                </svg>
                <span>{{ highlight }}</span>
              </li>
            </ul>
          </div>
        </div>
      </div>

      <!-- Additional Certifications or Achievements -->
      <div class="mt-16 reveal">
        <h3 class="font-display text-3xl font-bold text-center mb-8 text-gray-800 dark:text-gray-200">
          Continuous <span class="text-gradient">Learning</span>
        </h3>
        <div class="grid md:grid-cols-2 gap-6">
          <div v-for="cert in certifications" :key="cert.title"
               class="flex items-start gap-4 p-6 bg-gradient-to-br from-soft-pink/50 to-beige/50 dark:from-dark-card/50 dark:to-dark-card rounded-xl hover:shadow-lg transition-all">
            <div class="w-12 h-12 bg-rose-gold/20 rounded-lg flex items-center justify-center flex-shrink-0">
              <svg class="w-6 h-6 text-rose-gold" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4M7.835 4.697a3.42 3.42 0 001.946-.806 3.42 3.42 0 014.438 0 3.42 3.42 0 001.946.806 3.42 3.42 0 013.138 3.138 3.42 3.42 0 00.806 1.946 3.42 3.42 0 010 4.438 3.42 3.42 0 00-.806 1.946 3.42 3.42 0 01-3.138 3.138 3.42 3.42 0 00-1.946.806 3.42 3.42 0 01-4.438 0 3.42 3.42 0 00-1.946-.806 3.42 3.42 0 01-3.138-3.138 3.42 3.42 0 00-.806-1.946 3.42 3.42 0 010-4.438 3.42 3.42 0 00.806-1.946 3.42 3.42 0 013.138-3.138z"></path>
              </svg>
            </div>
            <div>
              <h4 class="font-semibold text-gray-800 dark:text-gray-200 mb-1">{{ cert.title }}</h4>
              <p class="text-sm text-gray-600 dark:text-gray-400">{{ cert.description }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'EducationSection',
  data() {
    return {
      education: [
        {
          degree: 'Postgraduate Diploma in Information Technology',
          institution: 'Vaal University of Technology',
          period: '2025 – Present',
          status: 'In Progress',
          highlights: [
            'Advanced Software Engineering',
            'Cloud Architecture',
            'Data Science & Analytics'
          ]
        },
        {
          degree: 'Advanced Diploma in IT',
          institution: 'Vaal University of Technology',
          period: '2023',
          status: 'Completed',
          highlights: [
            'Web Development',
            'Database Management',
            'Systems Analysis'
          ]
        },
        {
          degree: 'Diploma in IT',
          institution: 'Vaal University of Technology',
          period: '2020 – 2022',
          status: 'Completed',
          highlights: [
            'Programming Fundamentals',
            'Software Development',
            'IT Infrastructure'
          ]
        }
      ],
      certifications: [
        {
          title: 'Vue.js Mastery',
          description: 'Advanced component architecture and state management'
        },
        {
          title: 'Laravel Development',
          description: 'Building scalable RESTful APIs and web applications'
        },
        {
          title: 'Agile Methodologies',
          description: 'Scrum and Kanban frameworks for team collaboration'
        },
        {
          title: 'Cloud Computing Fundamentals',
          description: 'AWS and Azure cloud services and deployment'
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

