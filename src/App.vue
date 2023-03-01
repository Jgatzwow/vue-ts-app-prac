<template>
  <div class="app">
    <header>
      <div class="order">
        <button @click="handleClick('title')">Order by title</button>
        <button @click="handleClick('salary')">Order by salary</button>
        <button @click="handleClick('location')">Order by location</button>
      </div>
    </header>
    <JobsList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import { Job } from "../types/Job";
import JobsList from "@/components/JobsList.vue";
import { OrderTerm } from "../types/OrderTerm";
export default defineComponent({
  name: "app",
  components: { JobsList },
  setup() {
    const jobs = ref<Job[]>([
      {
        title: "farm worker",
        location: "lon lon ranch",
        salary: 30000,
        id: "1",
      },
      {
        title: "baker",
        location: "Bakery",
        salary: 20000,
        id: "2",
      },
      {
        title: "fisherman",
        location: "some lake",
        salary: 10000,
        id: "3",
      },
      {
        title: "musician",
        location: "bar",
        salary: 40000,
        id: "4",
      },
      {
        title: "lumberjack",
        location: "some forest",
        salary: 50000,
        id: "5",
      },
    ]);
    const order = ref<OrderTerm>("title");
    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };
    return { jobs, handleClick, order };

    /*  const state = reactive({
      name: "Link",
      age: 25 as number | string,
    });
    state.name = "Michael";
    return { ...toRefs(state) };*/
    /*const name = ref("Link");
    const age = ref<number | string>(25);
    return { name, age };*/
  },
  methods: {},
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
  color: #50bd9b;
  border: 3px solid #5bc9a4;
  background: none;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
</style>
