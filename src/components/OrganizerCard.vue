<script setup lang="ts">
import type { Organizer } from '@/types'
defineProps<{ organizer: Organizer }>()
</script>

<template>
    <div class="cursor-pointer border border-gray-600 p-[20px] w-[250px] mb-[18px] hover:scale-101 hover:shadow-sp">
        <h2 class="text-xl">{{ organizer.name }}</h2>
        <span>@ {{ organizer.organization }} @ {{ organizer.location }}</span>
    </div>
</template>