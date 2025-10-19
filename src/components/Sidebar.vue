<script setup>
import { ref } from 'vue'
import { Menu, X, Home, Briefcase, PlusCircle } from 'lucide-vue-next'

const isOpen = ref(false)
const toggleSidebar = () => (isOpen.value = !isOpen.value)
</script>

<template>
  <div class="flex">
    <!-- Mobile toggle -->
    <button
      @click="toggleSidebar"
      class="md:hidden fixed top-4 left-4 z-50 bg-green-700 text-white p-2 rounded-md focus:outline-none"
    >
      <component :is="isOpen ? X : Menu" class="w-6 h-6" />
    </button>

    <!-- Sidebar -->
    <aside
      :class="[
        'fixed md:static top-0 left-0 h-full md:h-auto w-64 bg-gradient-to-b from-green-800 to-green-700 text-white transform transition-transform duration-300 ease-in-out z-40',
        isOpen ? 'translate-x-0' : '-translate-x-full md:translate-x-0'
      ]"
    >
      <div class="flex items-center justify-center p-6 border-b border-green-600">
        <h2 class="text-2xl font-bold tracking-wide">Vue Jobs</h2>
      </div>

      <nav class="mt-6 space-y-2 px-4">
        <a
          href="index.html"
          class="flex items-center px-3 py-2 rounded-lg hover:bg-green-600 transition"
        >
          <Home class="w-5 h-5 mr-3" />
          Home
        </a>
        <a
          href="jobs.html"
          class="flex items-center px-3 py-2 rounded-lg hover:bg-green-600 transition"
        >
          <Briefcase class="w-5 h-5 mr-3" />
          Jobs
        </a>
        <a
          href="add-job.html"
          class="flex items-center px-3 py-2 rounded-lg hover:bg-green-600 transition"
        >
          <PlusCircle class="w-5 h-5 mr-3" />
          Add Job
        </a>
      </nav>
    </aside>

    <!-- Main Content (Hero + rest of page) -->
    <div class="flex-1 md:ml-64">
      <slot />
    </div>
  </div>
</template>

<style scoped>
aside {
  box-shadow: 2px 0 6px rgba(0, 0, 0, 0.15);
}
</style>
