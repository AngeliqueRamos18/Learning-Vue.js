<script setup>
    import Hero from '@/components/Hero.vue'
    import HomeCards from '@/components/HomeCards.vue'
    import JobListings from '@/components/JobListings.vue';
</script>

<template>
    <!-- Refer to the file src/components/Hero.vue to check the default display output if the certain parameters were not called-->
    <Hero subtitle="Test Subtitle"/>
    <HomeCards />
    <!-- Based on the definedprops from JobListings.vue, this limits the showing of jobs in this page-->
    <JobListings :limit="3" :showButton="true"/>
</template>