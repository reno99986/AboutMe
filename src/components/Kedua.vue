<template>
  <div class="bg-gray-50 text-gray-900 font-sans">
    <!-- Navbar -->
    <nav class="fixed top-0 left-0 w-full z-50 bg-white border-b border-gray-300">
      <div class="flex justify-center space-x-8 py-4 text-lg">
        <a v-for="link in navLinks" :key="link.href" :href="link.href"
          class="relative text-gray-800 px-3 py-1 hover:bg-blue-100 hover:text-blue-600 transition rounded">
          {{ link.name }}
        </a>
      </div>
    </nav>

    <!-- Hero Section -->
    <section class="min-h-screen flex items-center justify-center bg-blue-50 text-center px-4">
      <div class="grid md:grid-cols-2 gap-8 items-center max-w-5xl w-full">
        <div class="text-left">
          <h2 class="text-4xl md:text-6xl font-bold mb-4 text-gray-900">Hi, I’m Reno</h2>
          <p class="text-lg md:text-xl text-gray-700 mb-6">
            6th Semester Computer Science student passionate about modern web development and machine learning.
          </p>
          <a href="#contact" class="inline-block bg-blue-600 text-white px-6 py-3 font-semibold hover:bg-blue-700 transition">Contact Me</a>
        </div>
        <!-- <div class="flex justify-center">
          <img src="https://via.placeholder.com/300x300" alt="Profile" class="w-60 h-60 object-cover border border-gray-300" />
        </div> -->
      </div>
    </section>

    <!-- About Section -->
    <section id="about" class="py-16 px-4 bg-white border-t border-gray-300">
      <div class="max-w-4xl mx-auto text-center">
        <h3 class="text-3xl font-bold mb-6 text-blue-600">About Me</h3>
        <p class="text-gray-700 leading-relaxed">
          6th Semester Computer Science student at Institut Teknologi Kalimantan. Passionate about software development, data science, and machine learning. Currently exploring backend architecture and building scalable web applications.
        </p>
      </div>
    </section>

    <!-- Skills Section -->
    <section id="skills" class="py-16 px-4 bg-gray-100 border-t border-gray-300">
      <div class="max-w-5xl mx-auto">
        <h3 class="text-3xl font-bold text-center mb-10 text-blue-600">Skills</h3>
        <div class="grid sm:grid-cols-1 md:grid-cols-3 gap-8">
          <div v-for="skill in skills" :key="skill.title">
            <h4 class="text-lg font-semibold text-center mb-4 text-gray-800">{{ skill.title }}</h4>
            <div class="flex flex-wrap justify-center gap-2">
              <span v-for="item in skill.items" :key="item"
                class="border border-gray-400 text-gray-700 text-sm px-3 py-1 hover:border-blue-600 hover:text-blue-600 transition">
                {{ item }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="py-16 px-4 bg-white border-t border-gray-300">
      <div class="max-w-6xl mx-auto">
        <h3 class="text-3xl font-bold mb-10 text-center text-blue-600">Projects</h3>
        <div class="grid gap-8 md:grid-cols-2">
          <div v-for="project in projects" :key="project.title"
            class="border border-gray-400 p-6 hover:border-blue-600 transition">
            <h4 class="text-xl font-semibold mb-2 text-gray-800">{{ project.title }}</h4>
            <p class="text-gray-700 mb-3">{{ project.description }}</p>
            <div class="flex flex-wrap gap-2 text-sm mb-3">
              <span v-for="tech in project.stack" :key="tech"
                class="border border-gray-400 text-gray-700 px-2 py-0.5 hover:border-blue-600 hover:text-blue-600 transition">
                {{ tech }}
              </span>
            </div>
            <span v-if="project.private" class="text-red-500 text-sm">-- Private Project --</span>
            <a v-else :href="project.link" class="text-blue-600 hover:underline text-sm" target="_blank">View Project →</a>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-16 px-4 bg-gray-100 border-t border-gray-300">
      <div class="max-w-4xl mx-auto text-center">
        <h3 class="text-3xl font-bold mb-4 text-blue-600">Contact Me</h3>
        <p class="text-gray-700 mb-6">Let's work together! Reach me on:</p>
        <div class="flex justify-center gap-6 text-lg">
          <a href="mailto:jamrock99986@gmail.com" class="hover:text-blue-600 hover:underline">Email</a>
          <a href="https://github.com/reno99986" target="_blank" class="hover:text-blue-600 hover:underline">GitHub</a>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
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
