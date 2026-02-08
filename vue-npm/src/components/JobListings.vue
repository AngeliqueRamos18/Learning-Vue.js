<script setup>
// Import data with json 
import jobData from '@/jobs.json'

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
    <section class="bg-blue-50 px-4 py-10">
        <div class="container-xl lg:container m-auto">
            <h2 class="text-3xl font-bold text-green-500 mb-6 text-center">
                Browse Jobs
            </h2>
            <div class="grid grid-cols-1 md:grip-cols-3 gap-6">
                <!-- Time to import the data with json on the design -->
                <JobListing div v-for="job in jobs.slice(0, limit || jobs.length)" :key="job.id" :job="job"/>
            </div>
        </div>
    </section>
    
    <section v-if="showButton" class="m-auto max-w-lg my-10 px-6">
      <a
        href="/jobs"
        class="block bg-black text-white text-center py-4 px-6 rounded-xl hover:bg-gray-700"
        >View All Jobs</a>
    </section>
</template>