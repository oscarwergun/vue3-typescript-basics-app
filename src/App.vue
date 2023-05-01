<template>
  <div id="app">
    <header>
      <h2 class="title">
        {{ title }}
      </h2>
      <img src="./assets/CodegURU.png" alt="logo">
    </header>
    <div class="buttons">
      <button @click="handleClick('title')">Order by title</button>
      <button @click="handleClick('location')">Order by location</button>
      <button @click="handleClick('salary')">Order by salary</button>
    </div>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from
  'vue';
import Job from './types/Job'
import OrderTerm from '@/types/OrderTerm'
import JobList from './components/JobList.vue'

export default defineComponent({
  name: 'App',
  components: { JobList },
  setup() {
    const title = ref('JobFinder')
    // TYPE DEFINITION AND IMPORT JOB INTERFACE 
    const jobs = ref<Job[]>([
      { title: 'front-end developer', location: 'Albania', salary: 35000, id: '1' },
      { title: 'full-stack developer', location: 'Denmark', salary: 39000, id: '2' },
      { title: 'JR front-end developer', location: 'Sweden', salary: 32000, id: '3' },
      { title: 'Sales Manager', location: 'Sweden', salary: 38000, id: '4' }
    ])

    const order = ref<OrderTerm>('title')
    const handleClick = (term: OrderTerm) => {
      order.value = term
    }
    return { jobs, title, handleClick, order }
  }
},
);
</script>

<style scoped>
#app {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

header {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 80%;
  gap: 20px;
}

header img {
  width: 120px;
  border-radius: 50%;
  margin: 10px;
}

header .title {
  font-weight: 800;
  font-style: italic;
  letter-spacing: 2px;
  font-family: 'Comic Neue', cursive;
  font-size: 36px;
}

.buttons button {
  margin: 0 5px;
  padding: 8px 16px;
  border-radius: 10px;
  border: 2px solid var(--salary);
  background: var(--salary);
  color: var(--list-bg);
  opacity: 90%;
  cursor: pointer;
  font-weight: 600;

}
</style>
