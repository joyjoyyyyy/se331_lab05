<script setup lang="ts">
import type {Student} from '@/types'
import StudentCard from '@/components/StudentCard.vue'
import StudentService from '@/services/StudentService'
import { onMounted, ref } from 'vue'
const students = ref<Student[]>([])

onMounted(() => {
  StudentService.getStudents()
    .then(({data}: {data: Student[]}) => {
      //console.log(response.data)
      students.value = data
    })
})
</script>

<template>
    <h2>Student View</h2>

    <div class="card-container">
        <StudentCard v-for="student in students" :key="student.id" :student="student" />
    </div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>