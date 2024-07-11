<script setup lang="ts">
import EventCard from '@/components/EventCard.vue'
import ShowName from '@/components/ShowName.vue'
import Event from '@/types/Event'
import { ref } from 'vue'

const events = ref<Event []>([
  {
  id: 5928101,
  category: 'animal welfare',
  title: 'Cat Adoption Day',
  description: 'Find your new feline friend at this event',
  location: 'Meow Town',
  date: 'January 28, 2022',
  time: '12:00',
  petsAllowed: true,
  organizer: 'Kat Laydee'
},
{
  id: 4582797,
  category: 'food',
  title: 'Community Gardening',
  description: 'Join us as we tend to the community edible plants',
  location: 'Flora City',
  date: 'March 14, 2022',
  time: '10:00',
  petsAllowed: true,
  organizer: 'Fern Pollin'
},
{
  id: 3928101,
  category: 'education',
  title: 'Coding Bootcamp',
  description: 'Learn to code in a supportive environment',
  location: 'Tech Town',
  date: 'April 2, 2022',
  time: '09:00',
  petsAllowed: false,
  organizer: 'Code Cadet'
}])

const showName = ref<Event []>([
  {
  category: 'animal welfare',
  organizer: 'Fern Pollin',
},
{
  category: 'food',
  organizer: 'Kat Laydee',
},
{
  category: 'education',
  organizer: 'Code Cadet',
}
])
</script>

<template>
  <h1>Events For Good</h1>
<!-- new element-->
  <div class="home">
    <EventCard v-for="event in events" :key="event.id" :event="event"/>
    <ShowName v-for="event in showName" :key="event.category" :event="event"/>
  </div>
</template>


<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
