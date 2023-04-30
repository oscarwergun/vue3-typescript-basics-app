<template>
  <div id="app">
    <h2 class="title">
      {{ jobs[0].id }}
    </h2>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from
  'vue';
import Job from './types/Job'

export default defineComponent({
  name: 'App',
  components: {},
  setup() {
    
    // TYPE DEFINITION AND IMPORT JOB INTERFACE 
    const jobs = ref<Job[]>([
      { title: 'front-end developer', location: 'Sweden', salary: 35000, id: '1' },
      { title: 'full-stack developer', location: 'Denmark', salary: 38000, id: '2' },
      { title: 'JR front-end developer', location: 'Sweden', salary: 32000, id: '3' },
      { title: 'Sales Manager', location: 'Sweden', salary: 38000, id: '4' }
    ])
    return {jobs}
  }
},
);
</script>

<style>
#app {
  display: flex;
  align-items: center;
  justify-content: center;
}

.title {
  font-weight: 500;
  font-style: italic;
}
</style>
