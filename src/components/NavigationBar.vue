<template>
  <nav :class="[
    'fixed top-0 left-0 right-0 z-50 transition-all duration-300', isScrolled ? 'bg-white/90 ' : 'bg-transparent'
  ]">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex  items-center h-20">

        <!-- Desktop Navigation -->
        <div class="hidden md:flex items-center gap-8">
          <a v-for="link in navLinks" :key="link.name"
             :href="link.href"
             @click="setActiveLink(link.name)"
             :class="[
               'text-sm font-semibold transition-all duration-300 relative group',
               activeLink === link.name 
                 ? 'text-[#b76e79]' 
                 : 'text-gray-700  hover:text-[#b76e79]'
             ]">
            {{ link.name }}
            <span :class="[
              'absolute bottom-0 left-0 w-full h-0.5 bg-[#b76e79] transform origin-left transition-transform duration-300',
              activeLink === link.name ? 'scale-x-100' : 'scale-x-0 group-hover:scale-x-100'
            ]"></span>
          </a>
        </div>
      </div>

      <!-- Mobile Menu -->
      <transition name="slide-down">
        <div v-if="isMobileMenuOpen" class="md:hidden py-4 border-t border-gray-200">
          <div class="flex flex-col gap-4">
            <a v-for="link in navLinks" :key="link.name"
               :href="link.href"
               @click="handleMobileClick(link.name)"
               :class="[
                 'px-4 py-2 rounded-lg font-semibold transition-all',
                 activeLink === link.name 
                   ? 'bg-[#b76e79] text-white' 
                   : 'text-gray-700 hover:bg-[#b76e79]/20'
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
      isMobileMenuOpen: false,
      activeLink: 'Home',
      navLinks: [
        { name: 'Home', href: '#home' },
        { name: 'Experience', href: '#experience' },
        { name: 'Education', href: '#education' },
        { name: 'Skills', href: '#skills' },
        { name: 'Projects', href: '#projects' },
        { name: 'About', href: '#about' },
        { name: 'Contact', href: '#contact' }
      ]
    }
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
    this.observeSections();
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    handleScroll() {
      this.isScrolled = window.scrollY > 50;
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

