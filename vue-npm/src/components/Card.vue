<script setup>
    import { defineProps } from 'vue';

    defineProps({
        bg:{
            type: String,
            default: 'bg-gray-100'
        }
    });
</script>

<template>
    <!--To make it dynamic on the class put a : on the class to bind (:class)-->
    <!--Then insert double quote and wrap with ` to make it the entire line as javascript-->
    <div :class="`${bg} p-6 rounded-lg shadow-md`">
        <slot></slot>
    </div>
</template>