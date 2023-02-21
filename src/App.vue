<template>
  <div class="app">
    <header>
      <div class="title">
        <img src="./assets/heart.svg" alt="site logo">
        <h1>Hyrule Jobs</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">Order by title</button>
        <button @click="handleClick('salary')">Order by salary</button>
        <button @click="handleClick('location')">Order by location</button>
      </div>
    </header>
   <JobList :jobs="jobs" :order="order"/>
  </div>
</template>
<script lang="ts">

import { defineComponent,ref } from 'vue';
import { Job } from './types/job';
import JobList from './components/jobsList.vue'
import { OrderTerm } from './types/OrderTerm';
export default defineComponent({
  name: 'App',
  components: {JobList},
  setup() {

    const jobs = ref<Job[] >([
     {title: 'farm worker', location: "France", salary: 1200, id: "1"},
     {title: 'quarryman', location: "London", salary: 1100, id: "2"},
     {title: 'flute player', location: "Spain", salary: 1500, id: "3"},
     {title: 'prison guard', location: "Italy", salary: 1800, id: "4"}
    ])

    const order = ref<OrderTerm>('title')

    const handleClick= (term: OrderTerm) => {
       order.value = term
    }

    return {jobs, handleClick, order}
   
  },
  methods: {
 
  }
  
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
  header .title{
    display: flex;
    justify-content: center;
  }
  header img {
    width: 60px;
    margin-right: 20px;
  }
  header h1 {
    font-size: 3em;
  }
</style>
