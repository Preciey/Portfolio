<script setup>
import NavigationBar from './components/NavigationBar.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import SkillsSection from './components/SkillsSection.vue'
import ProjectsSection from './components/ProjectsSection.vue'
import ExperienceSection from './components/ExperienceSection.vue'
import EducationSection from './components/EducationSection.vue'
import ContactSection from './components/ContactSection.vue'
import FooterSection from './components/FooterSection.vue'
import FloatingButton from './components/FloatingButton.vue'
</script>

<template>
  <div class="min-h-screen">
    <!-- Navigation -->
    <NavigationBar />

    <!-- Main Content -->
    <main>
      <HeroSection />
      <AboutSection />
      <SkillsSection />
      <ProjectsSection />
      <ExperienceSection />
      <EducationSection />
      <ContactSection />
    </main>

    <!-- Footer -->
    <FooterSection />

    <!-- Floating Connect Button -->
    <FloatingButton />
  </div>
</template>

<style>
/* Global styles are in main.css */
</style>

