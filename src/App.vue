<script setup>
import Navber from './components/Navber.vue';
import Hero from './components/Hero.vue';
import HomeCard from './components/HomeCard.vue';
import JobListings from './components/JobListings.vue';
</script>
<template>
   <Navber />
   <Hero />
   <HomeCard />
   <JobListings :limit="3" :showButton="true" />
</template>