<script setup lang="ts">
import { onMounted, ref, toRefs } from 'vue'
import type {Event} from '@/types'
import { useRouter } from 'vue-router';
import { useMessageStore } from '@/stores/message';
import EventService from '@/services/EventService';

const props = defineProps<{
  id: string
}>()
//eslint-disable-next-line @typescript-eslint/no-unused-vars
const event = ref<Event | null>(null)

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
const router = useRouter()
const store = useMessageStore()
const register = () => {
  //if the registeration API is successful , push back to the event detail view
  store.updateMessage('You are successfully registered for ' + event.value?.title)   

setTimeout(() => { 
  store.resetMessage()
}, 3000)
router.push ({ name: 'event-detail-view', params: { id: event.value?.id }})
}
</script>
<template>
    <p>Register event here</p>
    <button @click="register">Register</button>
</template>
