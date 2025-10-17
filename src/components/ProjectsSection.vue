<template>
  <section id="projects" class="section-container bg-white dark:bg-dark-bg">
    <div class="max-w-7xl mx-auto">
      <!-- Section Title -->
      <h2 class="section-title reveal">
        Featured <span class="text-gradient">Projects</span>
      </h2>

      <!-- Projects Grid -->
      <div class="grid md:grid-cols-2 gap-8 mt-12">
        <div v-for="(project, index) in projects" :key="index" 
             class="card reveal group relative overflow-hidden"
             :style="{ animationDelay: `${index * 0.1}s` }"
             @mouseenter="hoveredProject = index"
             @mouseleave="hoveredProject = null">
          
          <!-- Project Image Placeholder -->
          <div class="relative h-64 bg-gradient-to-br from-rose-gold/20 to-pink-300/20 rounded-xl mb-6 overflow-hidden">
            <div class="absolute inset-0 flex items-center justify-center">
              <svg class="w-24 h-24 text-rose-gold/30" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path>
              </svg>
            </div>
            
            <!-- Code Snippet Overlay on Hover -->
            <div v-if="hoveredProject === index" 
                 class="absolute inset-0 bg-dark-bg/95 backdrop-blur-sm flex items-center justify-center p-6 animate-fade-in">
              <pre class="text-xs text-green-400 font-mono overflow-hidden">
<code>{{ project.codeSnippet }}</code>
              </pre>
            </div>
          </div>

          <!-- Project Info -->
          <div class="space-y-4">
            <h3 class="font-display text-2xl font-semibold text-gray-800 dark:text-gray-200 group-hover:text-rose-gold transition-colors">
              {{ project.title }}
            </h3>
            <p class="text-gray-600 dark:text-gray-400 leading-relaxed">
              {{ project.description }}
            </p>

            <!-- Tech Stack Tags -->
            <div class="flex flex-wrap gap-2 pt-2">
              <span v-for="tech in project.techStack" :key="tech"
                    class="px-3 py-1 bg-rose-gold/10 dark:bg-rose-gold/20 text-rose-gold text-xs font-semibold rounded-full">
                {{ tech }}
              </span>
            </div>

            <!-- Project Links -->
            <div class="flex gap-4 pt-4">
              <a href="#" class="text-rose-gold hover:text-rose-gold/80 transition-colors flex items-center gap-2 text-sm font-semibold">
                <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"></path>
                </svg>
                View Project
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ProjectsSection',
  data() {
    return {
      hoveredProject: null,
      projects: [
        {
          title: 'Clear Access Library System',
          description: 'Built responsive components with Vue.js, implemented CRUD tables for efficient data management, and integrated REST APIs for seamless backend communication.',
          techStack: ['Vue.js', 'Laravel', 'MySQL', 'REST API'],
          codeSnippet: `// Vue Component\nexport default {\n  async fetchBooks() {\n    const response = await\n    api.get('/books');\n    this.books = response.data;\n  }\n}`
        },
        {
          title: 'SACAI Admin Portal',
          description: 'Designed and developed an ad hoc billing module with Laravel backend, featuring dynamic invoice generation and comprehensive payment tracking.',
          techStack: ['Laravel', 'PHP', 'MySQL', 'Tailwind CSS'],
          codeSnippet: `// Laravel Controller\npublic function generateInvoice($id)\n{\n  $billing = Billing::find($id);\n  return view('invoice',\n    compact('billing'));\n}`
        },
        {
          title: 'Portfolio Template Market',
          description: 'Created custom navigation system and responsive UI for Ecwid e-commerce platform, enhancing user experience and conversion rates.',
          techStack: ['JavaScript', 'HTML5', 'CSS3', 'Ecwid API'],
          codeSnippet: `// Custom Navigation\nconst nav = {\n  init() {\n    this.setupMenu();\n    this.handleScroll();\n  }\n}`
        },
        {
          title: 'Mimie Scents',
          description: 'Personal project featuring an elegant landing page for a boutique fragrance brand, built with modern web technologies and smooth animations.',
          techStack: ['React', 'Tailwind CSS', 'Framer Motion'],
          codeSnippet: `// React Component\nfunction Hero() {\n  return (\n    <motion.div\n      initial={{ opacity: 0 }}\n      animate={{ opacity: 1 }}\n    />\n  );\n}`
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

