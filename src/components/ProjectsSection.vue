<template>
  <section id="projects" class="section-container bg-rose-50/60 pb-24">
    <div class="max-w-5xl mx-auto">

      <!-- Title -->
      <h2 class="section-title text-4xl font-bold text-[#b76e79] text-center pt-12">
        Featured Projects
      </h2>

      <!-- Grid -->
      <div class="grid md:grid-cols-2 gap-8 mt-12">

        <div
          v-for="(project, index) in projects"
          :key="index"
          class="card reveal group relative overflow-hidden shadow-md rounded-md bg-white"
          :style="{ animationDelay: `${index * 0.1}s` }"
          @mouseenter="hoveredProject = index"
          @mouseleave="hoveredProject = null"
        >

          <!-- IMAGE -->
          <div class="relative h-64 overflow-hidden rounded-t-md">

            <img
              :src="project.image"
              :alt="project.title"
              class="w-full h-full object-cover transform group-hover:scale-105 transition duration-500"
            />

            <!-- Code Overlay -->
            <div
              v-if="hoveredProject === index"
              class="absolute inset-0 backdrop-blur-sm bg-black/40 flex items-center justify-center p-6"
            >
              <pre class="text-xs text-green-400 font-mono overflow-hidden">
<code>{{ project.codeSnippet }}</code>
              </pre>
            </div>

          </div>

          <!-- CONTENT -->
          <div class="p-6 space-y-4">

            <h3 class="font-display text-2xl font-semibold text-gray-800 group-hover:text-[#b76e79] transition-colors">
              {{ project.title }}
            </h3>

            <p class="text-gray-600 leading-relaxed">
              {{ project.description }}
            </p>

            <!-- TECH STACK -->
            <div class="flex flex-wrap gap-2 pt-2">
              <span
                v-for="tech in project.techStack"
                :key="tech"
                class="px-3 py-1 bg-[#b76e79]/10 text-[#b76e79] text-xs font-semibold rounded-full"
              >
                {{ tech }}
              </span>
            </div>

            <!-- LINKS -->
            <div class="flex gap-4 pt-4">

              <a
                :href="project.liveLink"
                target="_blank"
                class="text-[#b76e79] hover:text-[#b76e79]/80 transition-colors flex items-center gap-2 text-sm font-semibold"
              >
                <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                    d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14" />
                </svg>
                Live Project
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
          title: 'Personal Portfolio Website',
          description: 'A modern developer portfolio showcasing full-stack development skills, responsive design, and clean UI/UX.',
          techStack: ['Vue.js', 'Tailwind CSS', 'JavaScript', 'Vercel'],
          liveLink: 'https://preciey-portfolio.vercel.app/',
          image: '/images/portfolio.png',
          codeSnippet: `// Vue component structure
export default {
  name: 'Portfolio',
  data() {
    return {
      projects: []
    };
  },
  mounted() {
    this.initAnimations();
  }
}`
        },

        {
          title: 'ARKEN Studio Website',
          description: 'A premium architecture website with animations, custom cursor effects, and minimalist UI design.',
          techStack: ['HTML5', 'CSS3', 'JavaScript', 'CSS Grid'],
          liveLink: 'https://preciey.github.io/Arken-Project/',
          image: '/images/arken.png',
          codeSnippet: `// Scroll animation with IntersectionObserver
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('animate-in');
    }
  });
}, { threshold: 0.1 });

document.querySelectorAll('.reveal').forEach(el => {
  observer.observe(el);
});`
        },

        {
          title: 'SOHO Connect Website',
          description: 'A professional client website built for a business platform with responsive and clean UI design.',
          techStack: ['HTML5', 'CSS3', 'JavaScript'],
          liveLink: 'https://www.sohoconnect.co.za/',
          image: '/images/soho-connect.png',
          codeSnippet: `// Dynamic navigation handler
const links = document.querySelectorAll('nav a');

links.forEach(link => {
  link.addEventListener('click', (e) => {
    e.preventDefault();
    const target = document.querySelector(link.getAttribute('href'));
    target.scrollIntoView({ behavior: 'smooth' });
  });
});`
        },

        {
          title: 'Mimie Scents E-Commerce Store',
          description: 'Luxury fragrance store with modern UI and animations. Currently in development.',
          techStack: ['React', 'Tailwind CSS', 'Framer Motion'],
          liveLink: '#',
          image: '/images/mimie.png',
          codeSnippet: `// Product card component
function ProductCard({ product }) {
  return (
    <motion.div
      className="product-card"
      whileHover={{ scale: 1.05 }}
    >
      <h3>{product.name}</h3>
      <p>{product.price}</p>
    </motion.div>
  );
}`
        }
      ]
    }
  }
}
</script>