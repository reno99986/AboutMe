<template>
  <div class="bg-gray-50 text-gray-900 font-sans">
    <!-- Navbar -->
    <nav class="fixed top-0 left-0 w-full z-50 bg-white/50 backdrop-blur-md shadow-sm">
      <div class="flex justify-center space-x-8 py-4 text-lg">
        <a v-for="link in navLinks" :key="link.href" :href="link.href"
          class="relative !text-gray-800 after:absolute after:left-1/2 after:bottom-0 after:h-[2px] after:w-0 after:bg-green-500 after:transition-all after:duration-300 after:ease-out hover:after:w-full hover:after:left-0 hover:text-green-600">
          {{ link.name }}
        </a>
      </div>
    </nav>

    <!-- Hero Section -->
    <section class="min-h-screen flex items-center justify-center bg-gradient-to-l from-green-300 to-yellow-200 text-center px-4">
      <div>
        <h2 class="text-4xl md:text-6xl font-bold mb-4 text-gray-900">Hi, I’m Reno</h2>
      </div>
    </section>

    <!-- About Section -->
    <section id="about" class="py-16 px-8 bg-white">
      <div class="max-w-3xl mx-auto text-center md:text-left">
        <h3 class="text-2xl font-bold mb-6 text-center text-green-600">About Me</h3>
        <p class="text-gray-700 text-justify leading-relaxed">
          6th Semester Computer Science student at Institut Teknologi Kalimantan. Passionate about software development, data science, and machine learning.           
        </p>
      </div>
    </section>

    <!-- Skills Section -->
    <section id="skills" class="py-16 px-6 bg-gradient-to-l from-green-50 to-yellow-50">
      <div class="max-w-4xl mx-auto">
        <h3 class="text-2xl font-bold text-center mb-10 text-green-600">Skills</h3>
        <div class="grid md:grid-cols-3 gap-8">
          <div v-for="skill in skills" :key="skill.title">
            <h4 class="text-lg font-semibold text-center mb-4 text-green-700">{{ skill.title }}</h4>
            <div class="flex flex-wrap justify-center gap-2">
              <span v-for="item in skill.items" :key="item"
                class="bg-white border border-green-300 text-gray-800 text-sm px-3 py-1 rounded-full shadow-sm hover:bg-green-100 transition">
                {{ item }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="py-16 px-6 bg-white">
      <div class="max-w-5xl mx-auto">
        <h3 class="text-2xl font-bold mb-10 text-center text-green-600">Projects</h3>
        <div class="grid gap-8 md:grid-cols-2">
          <div v-for="project in projects" :key="project.title"
            class="bg-green-50 border border-green-200 rounded-xl p-6 shadow-sm hover:shadow-md transition">
            <h4 class="text-xl font-semibold mb-2 text-green-700">{{ project.title }}</h4>
            <p class="text-gray-700 mb-3">{{ project.description }}</p>
            <div class="flex flex-wrap gap-2 text-sm mb-3">
              <span v-for="tech in project.stack" :key="tech"
                class="bg-green-200 text-green-900 px-2 py-0.5 rounded-full">{{ tech }}</span>
            </div>
            <span v-if="project.private" class="text-red-500 text-sm">-- Private Project --</span>
            <a v-else :href="project.link" class="text-green-700 hover:underline text-sm" target="_blank">View Project →</a>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-16 px-8 bg-gradient-to-l from-green-50 to-yellow-50">
      <div class="max-w-3xl mx-auto text-center">
        <h3 class="text-2xl font-bold mb-4 text-green-600">Contact Me</h3>
        <p class="text-gray-700 mb-4">Let's work together! Reach me on:</p>
        <div class="flex justify-center gap-6 text-2xl">
          <a href="mailto:rionandosoeksinputra@gmail.com" class="hover:text-green-700">Email</a>
          <a href="https://github.com/azureeeeeeeeeeee" target="_blank" class="hover:text-green-700">GitHub</a>
          <a href="https://instagram.com/_rio.nndo" target="_blank" class="hover:text-green-700">Instagram</a>
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
