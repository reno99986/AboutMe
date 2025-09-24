<template>
  <div class="bg-gray-50 text-gray-900 font-sans">
    <!-- Mobile Menu Button -->
    <div class="fixed top-4 right-4 z-50 md:hidden">
      <button @click="toggleMobileMenu" class="bg-white p-2 rounded-md shadow-lg border border-gray-300">
        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path v-if="!isMobileMenuOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
          <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
        </svg>
      </button>
    </div>

    <!-- Navbar -->
    <nav class="fixed top-0 left-0 w-full z-40 bg-white border-b border-gray-300">
      <!-- Desktop Navigation -->
      <div class="hidden md:flex justify-center space-x-8 py-4 text-lg">
        <a v-for="link in navLinks" :key="link.href" :href="link.href"
          class="relative text-gray-800 px-3 py-1 hover:bg-blue-100 hover:text-blue-600 transition rounded">
          {{ link.name }}
        </a>
      </div>
      
      <!-- Mobile Navigation -->
      <div v-if="isMobileMenuOpen" class="md:hidden bg-white border-t border-gray-200 py-2">
        <div class="flex flex-col space-y-2 px-4">
          <a v-for="link in navLinks" :key="link.href" :href="link.href"
            @click="closeMobileMenu"
            class="text-gray-800 px-3 py-2 hover:bg-blue-100 hover:text-blue-600 transition rounded text-center">
            {{ link.name }}
          </a>
        </div>
      </div>
    </nav>

    <!-- Hero Section -->
    <section class="min-h-screen flex items-center justify-center bg-blue-50 text-center px-4 pt-16">
      <div class="grid md:grid-cols-2 gap-8 items-center max-w-5xl w-full">
        <div class="text-center md:text-left">
          <h2 class="text-3xl sm:text-4xl md:text-6xl font-bold mb-4 text-gray-900">Hi, I'm Reno</h2>
          <p class="text-base sm:text-lg md:text-xl text-gray-700 mb-6 px-2">
            6th Semester Computer Science student passionate about modern web development and machine learning.
          </p>
          <a href="#contact" class="inline-block bg-blue-600 text-white px-6 py-3 font-semibold hover:bg-blue-700 transition rounded">Contact Me</a>
        </div>
      </div>
    </section>

    <!-- About Section -->
    <section id="about" class="py-12 md:py-16 px-4 bg-white border-t border-gray-300">
      <div class="max-w-4xl mx-auto text-center">
        <h3 class="text-2xl md:text-3xl font-bold mb-6 text-blue-600">About Me</h3>
        <p class="text-sm sm:text-base text-gray-700 leading-relaxed px-2">
          6th Semester Computer Science student at Institut Teknologi Kalimantan. Passionate about software development, data science, and machine learning. Currently exploring backend architecture and building scalable web applications.
        </p>
      </div>
    </section>

    <!-- Skills Section -->
    <section id="skills" class="py-12 md:py-16 px-4 bg-gray-100 border-t border-gray-300">
      <div class="max-w-5xl mx-auto">
        <h3 class="text-2xl md:text-3xl font-bold text-center mb-8 md:mb-10 text-blue-600">Skills</h3>
        <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-6 md:gap-8">
          <div v-for="skill in skills" :key="skill.title" class="bg-white p-4 rounded-lg shadow-sm border border-gray-200">
            <h4 class="text-base md:text-lg font-semibold text-center mb-4 text-gray-800">{{ skill.title }}</h4>
            <div class="flex flex-wrap justify-center gap-2">
              <span v-for="item in skill.items" :key="item"
                class="border border-gray-400 text-gray-700 text-xs sm:text-sm px-2 sm:px-3 py-1 hover:border-blue-600 hover:text-blue-600 transition rounded">
                {{ item }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="py-12 md:py-16 px-4 bg-white border-t border-gray-300">
      <div class="max-w-6xl mx-auto">
        <h3 class="text-2xl md:text-3xl font-bold mb-8 md:mb-10 text-center text-blue-600">Projects</h3>
        <div class="grid gap-6 md:gap-8 grid-cols-1 lg:grid-cols-2">
          <div v-for="project in projects" :key="project.title"
            class="border border-gray-400 p-4 md:p-6 hover:border-blue-600 transition rounded-lg bg-white shadow-sm">
            <h4 class="text-lg md:text-xl font-semibold mb-2 text-gray-800">{{ project.title }}</h4>
            <p class="text-sm md:text-base text-gray-700 mb-3 leading-relaxed">{{ project.description }}</p>
            <div class="flex flex-wrap gap-1 md:gap-2 text-xs md:text-sm mb-3">
              <span v-for="tech in project.stack" :key="tech"
                class="border border-gray-400 text-gray-700 px-2 py-0.5 hover:border-blue-600 hover:text-blue-600 transition rounded">
                {{ tech }}
              </span>
            </div>
            <span v-if="project.private" class="text-red-500 text-xs md:text-sm">-- Private Project --</span>
            <a v-else :href="project.link" class="text-blue-600 hover:underline text-xs md:text-sm" target="_blank">View Project →</a>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-12 md:py-16 px-4 bg-gray-100 border-t border-gray-300">
      <div class="max-w-4xl mx-auto text-center">
        <h3 class="text-2xl md:text-3xl font-bold mb-4 text-blue-600">Contact Me</h3>
        <p class="text-sm md:text-base text-gray-700 mb-6">Let's work together! Reach me on:</p>
        <div class="flex flex-col sm:flex-row justify-center gap-4 sm:gap-6 text-base md:text-lg">
          <a href="mailto:jamrock99986@gmail.com" class="bg-white px-4 py-2 rounded-lg border border-gray-300 hover:text-blue-600 hover:border-blue-600 transition">Email</a>
          <a href="https://github.com/reno99986" target="_blank" class="bg-white px-4 py-2 rounded-lg border border-gray-300 hover:text-blue-600 hover:border-blue-600 transition">GitHub</a>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const isMobileMenuOpen = ref(false)

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const closeMobileMenu = () => {
  isMobileMenuOpen.value = false
}

const navLinks = [
  { name: 'About', href: '#about' },
  { name: 'Skills', href: '#skills' },
  { name: 'Projects', href: '#projects' },
  { name: 'Contact', href: '#contact' },
]

const skills = [
  { title: 'Languages', items: ['Python', 'JavaScript'] },
  { title: 'Frameworks', items: ["Express", 'Vue', 'React'] },
  { title: 'Tools', items: ['Git', 'VS Code', 'MySQL', 'Docker'] },
]

const projects = [
  { title: 'Etamcode-forum', description: 'Forum web app built with Adonis and Vue.', stack: ['Javascript', 'Adonis', 'Vue'], link: '', private: true },
  { title: 'Permit and Obligation Management', description: 'Web App for managing and reminding users about Permit and Obligations', stack: ['ExpressJS', 'Nuxt',"Flowbite"], link: 'https://github.com/Magang-PT-IMM/FE-IMM', private: true },
  { title: 'Information System for RT45', description: 'CMS web for documenting and publicating RT45 Activity', stack: ['Nuxt', 'Django'], link: 'https://github.com/kkn2025-lebahmadu-itk/cms-kknlebahmadu-frontend', private: false },
]
</script>
