<template>
  <div class="app">
    <header>
      <div class="order">
        <button @click="handleClick('title')">order by title</button>
        <button @click="handleClick('salary')">order by salary</button>
        <button @click="handleClick('location')">order by location</button>
      </div>
    </header>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, /*reactive, toRefs,*/ ref } from "vue";
import JobList from "./components/JobsList.vue";
import Job from "./types/Job";
import OrderTerm from "./types/OrderTerm";

export default defineComponent({
  name: "App",
  components: { JobList },
  setup() {
    const jobs = ref<Job[]>([
      {
        title: "farmworker",
        location: "Lon Lon Ranch",
        salary: 30000,
        id: "1",
      },
      {
        title: "quarryman",
        location: "Death Mountain",
        salary: 40000,
        id: "2",
      },
      {
        title: "flute player",
        location: "The Lost Woods",
        salary: 35000,
        id: "3",
      },
      {
        title: "fisherman",
        location: "Lake Hylia",
        salary: 21000,
        id: "4",
      },
      {
        title: "prison guard",
        location: "Gerudo Valley",
        salary: 32000,
        id: "5",
      },
    ]);

    const order = ref<OrderTerm>("title");

    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };

    return { jobs, handleClick, order };
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

button:hover {
  color: #d9e9f0;
  border: 3px solid #094c66;
  background: #1a597e;
}
</style>
