<script setup>
import { defineProps, ref, computed} from 'vue';
import { RouterLink } from 'vue-router';
//this will be used as defineprop from JobListings.vue which takes in the value of the json data
const props = defineProps({
    job: Object
});

// set the variable wrapped with ref() if you are planning to make it reactive
const showFullDescription = ref(false);

// Pass a function
const truncatedDescription = computed(() => {
    let description = props.job.description;
    // dont forget .value at the end of the variable whenever you initially set the variable with ref()
    if (!showFullDescription.value) {
        // This will set the truncation of the desc if it's too long
        description = description.substring(0, 90).trim() + '...';
    }
    return description;
});

const toggleFullDescription = () => {
    showFullDescription.value = !showFullDescription.value;
};
</script>

<template>
<div class="relative bg-white shadow-md rounded-xl">
    <div class="p-4">
        <div class="mb-6">
        <div class="my-2 text-gray-600">{{ job.type }}</div>
        <h3 class="text-xl font-bold">{{ job.title }}</h3>
        </div>

        <div class="mb-5">
            <div>
                {{ truncatedDescription }}
            </div>
            <button @click="toggleFullDescription" class="mb-2 text-green-500 hover:text-green-600">
                {{ showFullDescription ? 'Less' : 'More' }}
            </button>
        </div>

        <h3 class="mb-2 text-green-500">{{ job.location }} / Year</h3>

        <div class="mb-5 border border-gray-100"></div>

        <div class="flex flex-col justify-between mb-4 lg:flex-row">
        <div class="mb-3 text-orange-700">
            <i class="text-orange-700 pi pi-map-marker"></i>
            {{ job.location }}
        </div>
        <!-- This is the part for route that depends on the id where to navigate you-->
        <RouterLink
            :to="'/jobs/' + job.id"
            class="h-[36px] bg-green-500 hover:bg-green-600 text-white px-4 py-2 rounded-lg text-center text-sm"
        >
            Read More
        </RouterLink>
        </div>
    </div>
</div>
</template>