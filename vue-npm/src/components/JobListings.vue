<script setup>
// Import data with json 
import jobData from '@/jobs.json'
import { RouterLink } from 'vue-router';

//In order to make this data reactive since we are importing or deleting and such make a ref to it
import { ref, defineProps } from 'vue';
const jobs = ref(jobData);

//Let's try to see the value, you can see this from console log in browser
console.log(jobs.value);

//Import the card from JobListing.vue
import JobListing from './JobListing.vue';

// This time is to make a limit based on the defined props (limit the showing of jobs)
defineProps({
    limit: Number,
    showButton: {
        type: Boolean,
        default: false
    }
});
</script>

<template>
    <!--The trick on creating elements with class quickly is to start with the object instead of <div>...-->
    <!--Then in order to input multiple class it would look like this-->
    <!--section.bg-blue-50.px-4.py-10 then press enter-->
    <!--but if you want to start with div, just start with .-->
    <section class="px-4 py-10 bg-blue-50">
        <div class="m-auto container-xl lg:container">
            <h2 class="mb-6 text-3xl font-bold text-center text-green-500">
                Browse Jobs
            </h2>
            <div class="grid grid-cols-1 gap-6 md:grip-cols-3">
                <!-- Time to import the data with json on the design -->
                <JobListing div v-for="job in jobs.slice(0, limit || jobs.length)" :key="job.id" :job="job"/>
            </div>
        </div>
    </section>
    
    <section v-if="showButton" class="max-w-lg px-6 m-auto my-10">
      <RouterLink
        to="/jobs"
        class="block px-6 py-4 text-center text-white bg-black rounded-xl hover:bg-gray-700"
        >View All Jobs</RouterLink>
    </section>
</template>