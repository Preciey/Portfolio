<template>
  <transition name="fade">
    <a v-if="isVisible"
       href="#contact"
       class="fixed bottom-8 right-8 z-40 w-14 h-14 bg-gradient-to-br from-rose-gold to-pink-400 rounded-full flex items-center justify-center shadow-2xl hover:scale-110 transition-all duration-300 animate-glow group"
       aria-label="Let's Connect">
      <!-- Icon -->
      <svg class="w-6 h-6 text-white group-hover:rotate-12 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 12h.01M12 12h.01M16 12h.01M21 12c0 4.418-4.03 8-9 8a9.863 9.863 0 01-4.255-.949L3 20l1.395-3.72C3.512 15.042 3 13.574 3 12c0-4.418 4.03-8 9-8s9 3.582 9 8z"></path>
      </svg>
      
      <!-- Tooltip -->
      <span class="absolute right-16 bg-dark-bg text-white px-4 py-2 rounded-lg text-sm font-semibold whitespace-nowrap opacity-0 group-hover:opacity-100 transition-opacity duration-300 pointer-events-none">
        Let's Connect
      </span>
      
      <!-- Pulse Ring -->
      <span class="absolute inset-0 rounded-full bg-rose-gold animate-ping opacity-20"></span>
    </a>
  </transition>
</template>

<script>
export default {
  name: 'FloatingButton',
  data() {
    return {
      isVisible: false
    }
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    handleScroll() {
      // Show button after scrolling down 300px
      this.isVisible = window.scrollY > 300;
    }
  }
}
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>

