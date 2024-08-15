<script setup lang="ts">
import { onMounted, ref, toRefs } from 'vue';
import type {Event} from '@/types'
import { useMessageStore } from '@/stores/message';
import router from '@/router';
import EventService from '@/services/EventService';

const props = defineProps<{
  id: string
}>()
const event = ref<Event | null>(null)
const store = useMessageStore()


onMounted(() => {
  EventService.getEvent(parseInt(props.id))
    .then((response) => {
      event.value = response.data
      console.log(event.value);
      
    })
    .catch((error) => {
      if (error.response && error.response.status === 404) {
      router.push({
        name: '404-resource-view',
        params: {resource: 'event'}
      })
    } else {
      router.push({name: 'network-error-view'})
    }
    })
})
const edit = () => {
  store.updateMessage('Data has been updated' + event.value?.title)

setTimeout(() => { 
  store.resetMessage()
}, 3000)
  router.push ({ name: 'event-detail-view', params: { id: event.value?.id }})
}
</script>

<template>
  <p>Edit event here</p>
  <button @click="edit">Edit Here</button>
</template>

<style scoped>
</style>