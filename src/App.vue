<script setup>
import Hero from './components/Hero.vue';
import HomeCards from './components/HomeCards.vue';
import JobListings from './components/JobListings.vue';
import Navbar from './components/Navbar.vue';
import HorseRace from '@/components/HorseRace.vue'
</script>

<template>
  <Navbar />
  <Hero title="Test Title" subtitle="Dont test me" />
  <HomeCards />
  <JobListings :limit="3" :showButton="true" />
  <HorseRace />
</template>

