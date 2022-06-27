<template>
  <div class="app">
    <header>
      <div class="title">
        <h1>Hyrule Jobs</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">Order by title</button>
        <button @click="handleClick('salary')">Order by salary</button>
        <button @click="handleClick('location')">Order by location</button>
      </div>
    </header>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import JobList from './components/JobList.vue'
import Job from './types/job'
import OrderTerm from './types/OrderTerm'

export default defineComponent({
  name: 'App',
  components: { JobList },
  setup() {
    const jobs = ref<Job[]>([
      {title: 'farm worker', location: 'lon lon ranch', salary: 300000, id: '1'},
      {title: 'flute player', location: 'von lon ranch', salary: 200000, id: '2'},
      {title: 'Prison guard', location: 'tonam vongure', salary: 500000, id: '3'},
      {title: 'fisherman', location: 'Oststrasse', salary: 30000, id: '4'},
    ])

  const order = ref<OrderTerm>('title')

    const handleClick = (term: OrderTerm) => {
      order.value = term;
    }

    return {jobs, handleClick, order};
  },
  
});
</script>

<style>
  header {
    text-align: center;
  }
  header .order {
    margin-top: 20px;
  }
  button {
    margin: 0 10px;
    color: #1195c9;
    border: 3px solid #1195c9;
    background: #d5f0ff;
    padding: 8px 16px;
    border-radius: 4px;
    cursor: pointer;
    font-weight: bold;
  }
</style>
