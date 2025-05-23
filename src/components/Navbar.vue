<!-- src/components/Navbar.vue -->
<script setup>
import logo from '@/assets/img/logo2.svg'
</script>

<template>
  <nav class="bg-blue-700 border-b border-blue-500">
    <div class="container mx-auto flex items-center justify-between px-4 py-4">
      <!-- Logo -->
      <a href="/">
        <img :src="logo" alt="Logo" class="h-10 w-auto" />
      </a>

      <!-- Links -->
      <div class="flex space-x-4">
        <a
          href="/"
          class="bg-blue-900 text-white px-3 py-2 rounded-md hover:bg-blue-800"
        >
          Home
        </a>
        <a
          href="/jobs"
          class="bg-blue-900 text-white px-3 py-2 rounded-md hover:bg-blue-800"
        >
          Jobs
        </a>
        <a
          href="/jobs/add"
          class="bg-blue-900 text-white px-3 py-2 rounded-md hover:bg-blue-800"
        >
          Add Job
        </a>
      </div>
    </div>
  </nav>
</template>
