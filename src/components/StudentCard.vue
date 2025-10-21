<script setup lang="ts">
defineProps<{
  student: {
    name: string
    surname: string
    gpa: number
  }
}>()
</script>

<template>
  <div class="student-card">
    <h3>{{ student.name }} {{ student.surname }}</h3>
    <p>GPA: {{ student.gpa }}</p>
  </div>
</template>

<style scoped>
.student-card {
  background-color: #f5f5f5;
  border-radius: 8px;
  padding: 20px;
  margin: 10px 0;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  width: 300px;
}

h3 {
  margin-top: 0;
  color: #333;
}

p {
  color: #666;
  font-size: 16px;
}
</style>