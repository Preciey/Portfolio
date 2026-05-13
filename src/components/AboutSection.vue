<template>
  <section id="about" class="section-container bg-white py-20">

    <div class="max-w-6xl mx-auto px-6">

      <!-- Title -->
      <h2 class="text-4xl font-bold text-[#b76e79] text-center mb-14">
        About Me
      </h2>

      <div class="max-w-3xl mx-auto text-center space-y-10 reveal">

        <!-- Intro -->
        <div class="space-y-5">

          <p class="text-lg text-gray-700 leading-relaxed">
            I'm a
            <span class="font-semibold text-[#b76e79]">Full Stack Developer</span>
            focused on building scalable, high-performance web applications and modern digital experiences.
          </p>

          <p class="text-lg text-gray-700 leading-relaxed">
            I work primarily with <span class="font-semibold">Vue.js, Laravel, JavaScript, and SQL</span>, turning complex requirements into clean, efficient, and maintainable systems.
          </p>

        </div>

        <!-- SKILLS -->
        <div class="bg-rose-50 p-8 rounded-2xl shadow-md">

          <h3 class="text-xl font-semibold text-gray-800 mb-6">
            Beyond the Code
          </h3>

          <div class="flex flex-wrap justify-center gap-3">
            <span
              v-for="interest in interests"
              :key="interest"
              class="px-4 py-2 bg-white rounded-full text-sm text-gray-700 shadow-sm hover:bg-[#b76e79] hover:text-white transition"
            >
              {{ interest }}
            </span>
          </div>

        </div>

        <!-- QUOTE -->
        <div>
          <p class="font-handwriting text-3xl text-[#b76e79] leading-relaxed">
            “Building thoughtful, user-focused digital products with clean code and intentional design.”
          </p>
        </div>

      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "AboutSection",
  data() {
    return {
      interests: [
        "UI Design",
        "System Architecture",
        "API Development",
        "E-commerce Solutions",
        "Performance Optimization",
        "User Experience"
      ]
    };
  },
  mounted() {
    this.observeElements();
  },
  methods: {
    observeElements() {
      const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            entry.target.classList.add("active");
          }
        });
      }, { threshold: 0.1 });

      document.querySelectorAll(".reveal").forEach(el =>
        observer.observe(el)
      );
    }
  }
};
</script>