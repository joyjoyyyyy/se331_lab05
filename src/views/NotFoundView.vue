<script setup lang="ts">
import { defineProps,withDefaults } from 'vue'
const props = withDefaults(
    defineProps<{
        resourse: string
    }>(),
    {
        resourse: 'page'
    }
)
</script>

<template>
    <h1>Oops</h1>
    <h3>The {{resourse}} you're looking for is not here</h3>
    <router-link :to="{ name: 'event-list-view'}">Back to the event list</router-link>
</template>