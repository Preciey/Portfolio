<template>
  <nav :class="[
    'fixed top-0 left-0 right-0 z-50 transition-all duration-300',
    isScrolled ? 'bg-white/90 dark:bg-dark-bg/90 backdrop-blur-lg shadow-lg' : 'bg-transparent'
  ]">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between items-center h-20">
        <!-- Logo -->
        <a href="#home" class="font-display text-2xl font-bold">
          <span class="text-gradient">PR</span>
        </a>

        <!-- Desktop Navigation -->
        <div class="hidden md:flex items-center gap-8">
          <a v-for="link in navLinks" :key="link.name"
             :href="link.href"
             @click="setActiveLink(link.name)"
             :class="[
               'text-sm font-semibold transition-all duration-300 relative group',
               activeLink === link.name 
                 ? 'text-rose-gold' 
                 : 'text-gray-700 dark:text-gray-300 hover:text-rose-gold'
             ]">
            {{ link.name }}
            <span :class="[
              'absolute bottom-0 left-0 w-full h-0.5 bg-rose-gold transform origin-left transition-transform duration-300',
              activeLink === link.name ? 'scale-x-100' : 'scale-x-0 group-hover:scale-x-100'
            ]"></span>
          </a>
        </div>

        <!-- Dark Mode Toggle & Mobile Menu -->
        <div class="flex items-center gap-4">
          <!-- Dark Mode Toggle -->
          <button @click="toggleDarkMode"
                  class="w-10 h-10 rounded-lg bg-gray-200 dark:bg-dark-card flex items-center justify-center hover:bg-rose-gold/20 dark:hover:bg-rose-gold/20 transition-all group"
                  aria-label="Toggle dark mode">
            <svg v-if="!isDark" class="w-5 h-5 text-gray-700 group-hover:text-rose-gold transition-colors" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z"></path>
            </svg>
            <svg v-else class="w-5 h-5 text-yellow-400 group-hover:text-rose-gold transition-colors" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 3v1m0 16v1m9-9h-1M4 12H3m15.364 6.364l-.707-.707M6.343 6.343l-.707-.707m12.728 0l-.707.707M6.343 17.657l-.707.707M16 12a4 4 0 11-8 0 4 4 0 018 0z"></path>
            </svg>
          </button>

          <!-- Mobile Menu Button -->
          <button @click="toggleMobileMenu"
                  class="md:hidden w-10 h-10 rounded-lg bg-gray-200 dark:bg-dark-card flex items-center justify-center hover:bg-rose-gold/20 transition-all"
                  aria-label="Toggle menu">
            <svg v-if="!isMobileMenuOpen" class="w-6 h-6 text-gray-700 dark:text-gray-300" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
            </svg>
            <svg v-else class="w-6 h-6 text-gray-700 dark:text-gray-300" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
            </svg>
          </button>
        </div>
      </div>

      <!-- Mobile Menu -->
      <transition name="slide-down">
        <div v-if="isMobileMenuOpen" class="md:hidden py-4 border-t border-gray-200 dark:border-gray-700">
          <div class="flex flex-col gap-4">
            <a v-for="link in navLinks" :key="link.name"
               :href="link.href"
               @click="handleMobileClick(link.name)"
               :class="[
                 'px-4 py-2 rounded-lg font-semibold transition-all',
                 activeLink === link.name 
                   ? 'bg-rose-gold text-white' 
                   : 'text-gray-700 dark:text-gray-300 hover:bg-rose-gold/20'
               ]">
              {{ link.name }}
            </a>
          </div>
        </div>
      </transition>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'NavigationBar',
  data() {
    return {
      isScrolled: false,
      isDark: false,
      isMobileMenuOpen: false,
      activeLink: 'Home',
      navLinks: [
        { name: 'Home', href: '#home' },
        { name: 'About', href: '#about' },
        { name: 'Skills', href: '#skills' },
        { name: 'Projects', href: '#projects' },
        { name: 'Experience', href: '#experience' },
        { name: 'Education', href: '#education' },
        { name: 'Contact', href: '#contact' }
      ]
    }
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
    this.checkDarkMode();
    this.observeSections();
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    handleScroll() {
      this.isScrolled = window.scrollY > 50;
    },
    
    toggleDarkMode() {
      this.isDark = !this.isDark;
      if (this.isDark) {
        document.documentElement.classList.add('dark');
        localStorage.setItem('darkMode', 'true');
      } else {
        document.documentElement.classList.remove('dark');
        localStorage.setItem('darkMode', 'false');
      }
    },
    
    checkDarkMode() {
      const darkMode = localStorage.getItem('darkMode');
      if (darkMode === 'true' || (!darkMode && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
        this.isDark = true;
        document.documentElement.classList.add('dark');
      }
    },
    
    toggleMobileMenu() {
      this.isMobileMenuOpen = !this.isMobileMenuOpen;
    },
    
    setActiveLink(name) {
      this.activeLink = name;
    },
    
    handleMobileClick(name) {
      this.setActiveLink(name);
      this.isMobileMenuOpen = false;
    },
    
    observeSections() {
      const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            const sectionId = entry.target.id;
            const link = this.navLinks.find(l => l.href === `#${sectionId}`);
            if (link) {
              this.activeLink = link.name;
            }
          }
        });
      }, { threshold: 0.5 });

      // Observe all sections
      this.navLinks.forEach(link => {
        const sectionId = link.href.substring(1);
        const section = document.getElementById(sectionId);
        if (section) {
          observer.observe(section);
        }
      });
    }
  }
}
</script>

<style scoped>
.slide-down-enter-active,
.slide-down-leave-active {
  transition: all 0.3s ease;
}

.slide-down-enter-from {
  opacity: 0;
  transform: translateY(-10px);
}

.slide-down-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>

