<template>
  <section id="contact" class="section-container bg-gradient-to-b from-soft-pink/30 to-white dark:from-dark-card/30 dark:to-dark-bg relative overflow-hidden">
    <!-- Background Decoration -->
    <div class="absolute top-20 right-0 w-96 h-96 bg-rose-gold/10 rounded-full blur-3xl"></div>
    <div class="absolute bottom-20 left-0 w-96 h-96 bg-pink-300/10 rounded-full blur-3xl"></div>

    <div class="max-w-5xl mx-auto relative z-10">
      <!-- Section Title -->
      <h2 class="section-title reveal">
        Let's <span class="text-gradient">Connect</span>
      </h2>

      <p class="text-center text-xl text-gray-600 dark:text-gray-400 mb-12 reveal font-handwriting">
        "Let's build something exceptional together."
      </p>

      <div class="grid md:grid-cols-2 gap-12">
        <!-- Contact Form -->
        <div class="reveal">
          <form @submit.prevent="handleSubmit" class="space-y-6">
            <!-- Name Input -->
            <div>
              <label for="name" class="block text-sm font-semibold text-gray-700 dark:text-gray-300 mb-2">
                Your Name
              </label>
              <input 
                type="text" 
                id="name"
                v-model="form.name"
                :class="[
                  'w-full px-4 py-3 rounded-xl border-2 transition-all duration-300',
                  errors.name 
                    ? 'border-red-400 focus:border-red-500' 
                    : 'border-gray-200 dark:border-gray-700 focus:border-rose-gold',
                  'bg-white dark:bg-dark-card text-gray-900 dark:text-gray-100',
                  'focus:outline-none focus:ring-2 focus:ring-rose-gold/20'
                ]"
                placeholder="John Doe"
              >
              <p v-if="errors.name" class="mt-1 text-sm text-red-500">{{ errors.name }}</p>
            </div>

            <!-- Email Input -->
            <div>
              <label for="email" class="block text-sm font-semibold text-gray-700 dark:text-gray-300 mb-2">
                Email Address
              </label>
              <input 
                type="email" 
                id="email"
                v-model="form.email"
                :class="[
                  'w-full px-4 py-3 rounded-xl border-2 transition-all duration-300',
                  errors.email 
                    ? 'border-red-400 focus:border-red-500' 
                    : 'border-gray-200 dark:border-gray-700 focus:border-rose-gold',
                  'bg-white dark:bg-dark-card text-gray-900 dark:text-gray-100',
                  'focus:outline-none focus:ring-2 focus:ring-rose-gold/20'
                ]"
                placeholder="john@example.com"
              >
              <p v-if="errors.email" class="mt-1 text-sm text-red-500">{{ errors.email }}</p>
            </div>

            <!-- Subject Input -->
            <div>
              <label for="subject" class="block text-sm font-semibold text-gray-700 dark:text-gray-300 mb-2">
                Subject
              </label>
              <input 
                type="text" 
                id="subject"
                v-model="form.subject"
                :class="[
                  'w-full px-4 py-3 rounded-xl border-2 transition-all duration-300',
                  errors.subject 
                    ? 'border-red-400 focus:border-red-500' 
                    : 'border-gray-200 dark:border-gray-700 focus:border-rose-gold',
                  'bg-white dark:bg-dark-card text-gray-900 dark:text-gray-100',
                  'focus:outline-none focus:ring-2 focus:ring-rose-gold/20'
                ]"
                placeholder="Project Inquiry"
              >
              <p v-if="errors.subject" class="mt-1 text-sm text-red-500">{{ errors.subject }}</p>
            </div>

            <!-- Message Textarea -->
            <div>
              <label for="message" class="block text-sm font-semibold text-gray-700 dark:text-gray-300 mb-2">
                Message
              </label>
              <textarea 
                id="message"
                v-model="form.message"
                rows="5"
                :class="[
                  'w-full px-4 py-3 rounded-xl border-2 transition-all duration-300 resize-none',
                  errors.message 
                    ? 'border-red-400 focus:border-red-500' 
                    : 'border-gray-200 dark:border-gray-700 focus:border-rose-gold',
                  'bg-white dark:bg-dark-card text-gray-900 dark:text-gray-100',
                  'focus:outline-none focus:ring-2 focus:ring-rose-gold/20'
                ]"
                placeholder="Tell me about your project..."
              ></textarea>
              <p v-if="errors.message" class="mt-1 text-sm text-red-500">{{ errors.message }}</p>
            </div>

            <!-- Submit Button -->
            <button 
              type="submit"
              :disabled="isSubmitting"
              class="w-full btn-primary disabled:opacity-50 disabled:cursor-not-allowed flex items-center justify-center gap-2"
            >
              <span v-if="!isSubmitting">Send Message</span>
              <span v-else>Sending...</span>
              <svg v-if="!isSubmitting" class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3"></path>
              </svg>
            </button>

            <!-- Success Message -->
            <div v-if="submitSuccess" class="p-4 bg-green-100 dark:bg-green-900/30 text-green-700 dark:text-green-400 rounded-xl text-center">
              Thank you! Your message has been sent successfully.
            </div>
          </form>
        </div>

        <!-- Contact Information -->
        <div class="reveal space-y-8" style="animation-delay: 0.2s;">
          <!-- Contact Details -->
          <div class="card">
            <h3 class="font-display text-2xl font-bold text-gray-800 dark:text-gray-200 mb-6">
              Get in Touch
            </h3>
            
            <div class="space-y-4">
              <!-- Email -->
              <a href="mailto:rathabane.sikedi1@gmail.com" 
                 class="flex items-center gap-4 p-4 bg-soft-pink/50 dark:bg-dark-bg/50 rounded-xl hover:bg-rose-gold/20 transition-all group">
                <div class="w-12 h-12 bg-rose-gold/20 rounded-lg flex items-center justify-center group-hover:bg-rose-gold group-hover:scale-110 transition-all">
                  <svg class="w-6 h-6 text-rose-gold group-hover:text-white transition-colors" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path>
                  </svg>
                </div>
                <div>
                  <p class="text-sm text-gray-600 dark:text-gray-400">Email</p>
                  <p class="font-semibold text-gray-800 dark:text-gray-200">rathabane.sikedi1@gmail.com</p>
                </div>
              </a>

              <!-- Location -->
              <div class="flex items-center gap-4 p-4 bg-soft-pink/50 dark:bg-dark-bg/50 rounded-xl">
                <div class="w-12 h-12 bg-rose-gold/20 rounded-lg flex items-center justify-center">
                  <svg class="w-6 h-6 text-rose-gold" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"></path>
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"></path>
                  </svg>
                </div>
                <div>
                  <p class="text-sm text-gray-600 dark:text-gray-400">Location</p>
                  <p class="font-semibold text-gray-800 dark:text-gray-200">Centurion, South Africa</p>
                </div>
              </div>
            </div>
          </div>

          <!-- Social Links -->
          <div class="card">
            <h3 class="font-display text-2xl font-bold text-gray-800 dark:text-gray-200 mb-6">
              Connect on Social
            </h3>
            
            <div class="flex gap-4">
              <a href="#" class="w-12 h-12 bg-rose-gold/20 rounded-lg flex items-center justify-center hover:bg-rose-gold hover:scale-110 transition-all group">
                <svg class="w-6 h-6 text-rose-gold group-hover:text-white transition-colors" fill="currentColor" viewBox="0 0 24 24">
                  <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
                </svg>
              </a>
              <a href="#" class="w-12 h-12 bg-rose-gold/20 rounded-lg flex items-center justify-center hover:bg-rose-gold hover:scale-110 transition-all group">
                <svg class="w-6 h-6 text-rose-gold group-hover:text-white transition-colors" fill="currentColor" viewBox="0 0 24 24">
                  <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
                </svg>
              </a>
            </div>
          </div>

          <!-- Availability -->
          <div class="p-6 bg-gradient-to-br from-rose-gold to-pink-400 text-white rounded-2xl shadow-lg">
            <div class="flex items-center gap-3 mb-2">
              <div class="w-3 h-3 bg-green-400 rounded-full animate-pulse"></div>
              <p class="font-semibold">Available for Projects</p>
            </div>
            <p class="text-sm text-white/90">
              I'm currently open to new opportunities and collaborations. Let's create something amazing together!
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ContactSection',
  data() {
    return {
      form: {
        name: '',
        email: '',
        subject: '',
        message: ''
      },
      errors: {},
      isSubmitting: false,
      submitSuccess: false
    }
  },
  mounted() {
    this.observeElements();
  },
  methods: {
    validateForm() {
      this.errors = {};
      
      if (!this.form.name.trim()) {
        this.errors.name = 'Name is required';
      }
      
      if (!this.form.email.trim()) {
        this.errors.email = 'Email is required';
      } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(this.form.email)) {
        this.errors.email = 'Please enter a valid email';
      }
      
      if (!this.form.subject.trim()) {
        this.errors.subject = 'Subject is required';
      }
      
      if (!this.form.message.trim()) {
        this.errors.message = 'Message is required';
      }
      
      return Object.keys(this.errors).length === 0;
    },
    
    async handleSubmit() {
      if (!this.validateForm()) {
        return;
      }
      
      this.isSubmitting = true;
      
      // Simulate form submission
      setTimeout(() => {
        this.isSubmitting = false;
        this.submitSuccess = true;
        
        // Reset form
        this.form = {
          name: '',
          email: '',
          subject: '',
          message: ''
        };
        
        // Hide success message after 5 seconds
        setTimeout(() => {
          this.submitSuccess = false;
        }, 5000);
      }, 1500);
    },
    
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

