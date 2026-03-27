<template>
  <nav :class="[
    'fixed top-0 left-0 right-0 z-50 transition-all duration-300',
    isScrolled ? 'bg-white/90 backdrop-blur' : 'bg-transparent'
  ]">

    <div class="max-w-xl md:max-w-4xl lg:max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">

      <div class="flex items-center h-20 justify-between w-full">

        <!-- Desktop Navigation -->
        <div class="hidden md:flex items-center gap-8">
          <a v-for="link in navLinks"
             :key="link.name"
             :href="link.href"
             @click="setActiveLink(link.name)"
             :class="[
               'text-sm font-semibold transition-all duration-300 relative group',
               activeLink === link.name 
                 ? 'text-[#b76e79]' 
                 : 'text-gray-700 hover:text-[#b76e79]'
             ]">

            {{ link.name }}

            <span :class="[
              'absolute bottom-0 left-0 w-full h-0.5 bg-[#b76e79] transform origin-left transition-transform duration-300',
              activeLink === link.name 
                ? 'scale-x-100' 
                : 'scale-x-0 group-hover:scale-x-100'
            ]"></span>

          </a>
        </div>

        <!-- Mobile Menu Button -->
        <div class="md:hidden ml-auto">
          <button 
            @click="toggleMobileMenu"
            class="text-gray-700 hover:text-[#b76e79] transition">

            <svg xmlns="http://www.w3.org/2000/svg"
                 class="h-7 w-7"
                 fill="none"
                 viewBox="0 0 24 24"
                 stroke="currentColor">

              <!-- Hamburger -->
              <path v-if="!isMobileMenuOpen"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M4 6h16M4 12h16M4 18h16"/>

              <!-- Close -->
              <path v-else
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M6 18L18 6M6 6l12 12"/>

            </svg>

          </button>
        </div>

      </div>

      <!-- Mobile Menu -->
      <transition name="slide-down">
        <div v-if="isMobileMenuOpen"
             class="md:hidden py-4 border-t border-gray-200 bg-white/95 backdrop-blur">

          <div class="flex flex-col gap-4">

            <a v-for="link in navLinks"
               :key="link.name"
               :href="link.href"
               @click="handleMobileClick(link.name)"
               :class="[
                 'px-4 py-3 rounded-lg font-semibold transition-all',
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
      observer: null,

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

    if (this.observer) {
      this.observer.disconnect();
    }
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

      this.observer = new IntersectionObserver((entries) => {

        entries.forEach(entry => {

          if (entry.isIntersecting) {

            const sectionId = entry.target.id;

            const link = this.navLinks.find(
              l => l.href === `#${sectionId}`
            );

            if (link) {
              this.activeLink = link.name;
            }

          }

        });

      }, { threshold: 0.5 });


      this.navLinks.forEach(link => {

        const sectionId = link.href.substring(1);

        const section = document.getElementById(sectionId);

        if (section) {
          this.observer.observe(section);
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