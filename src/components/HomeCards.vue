<script setup>
import { RouterLink } from 'vue-router';
import Card from '@/components/Card.vue';
</script>

<template>
  <section class="py-4">
    <div class="container-xl lg:container m-auto">
      <div class="grid grid-cols-1 md:grid-cols-2 gap-4 p-4 rounded-lg">
        <Card>
          <h2 class="text-2xl font-bold">For Developers</h2>
          <p class="mt-2 mb-4">
            Browse our Vue jobs and start your career today
          </p>
          <a
          href="/"
          class="bg-blue-900 text-white px-3 py-2 rounded-md hover:bg-blue-800"
        >
          Browse Jobs
        </a>
        </Card>
        <Card bg="bg-green-100">
          <h2 class="text-2xl font-bold">For Employers</h2>
          <p class="mt-2 mb-4">
            List your job to find the perfect developer for the role
          </p>
           <a
          href="/"
          class="bg-blue-900 text-white px-3 py-2 rounded-md hover:bg-blue-800"
        >
          Add jobs
        </a>
        </Card>
      </div>
    </div>
  </section>
</template>