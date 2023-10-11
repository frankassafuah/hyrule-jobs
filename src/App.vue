<template>
  <!-- <div class="app">Hello {{ name }}, you are {{ age }} years old</div>
  <button @click="changeName('CLB')">change name</button>
  <button @click="changeAge('25')">change age</button> -->
  <div>
    <button @click="changeOrder('title')">order by title</button>
    <button @click="changeOrder('salary')">order by salary</button>
    <button @click="changeOrder('location')">order by location</button>
    <JobsList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import Job from "./types/Job";
import OrderTerm from "./types/OrderTerm";
import JobsList from "./components/JobsList.vue";
import orderTerm from "./types/OrderTerm";

export default defineComponent({
  name: "App",
  components: {
    JobsList,
  },

  //options API with Typescript
  // data() {
  //   return {
  //     name: "Frank",
  //     age: 23 as number | string, //type assertion or type casting (Union Type)
  //   };
  // },

  //Composition API with Typescript
  setup() {
    const name = ref("Link");
    const age = ref<number | string>(25); //type assertion or type casting (Union Type)
    const jobs = ref<Job[]>([
      {
        title: "Farm worker",
        location: "Ion ranch",
        salary: "3000",
        id: "1",
      },
      {
        title: "Fisherman ",
        location: "lake",
        salary: "3500",
        id: "2",
      },
      {
        title: "Prison guard",
        location: "gerudo valley",
        salary: "2300",
        id: "3",
      },
    ]);
    const order = ref<orderTerm>("title");

    const changeOrder = (term: OrderTerm) => {
      order.value = term;
    };

    return {
      name,
      age,
      jobs,
      changeOrder,
      order,
    };
  },
  // methods: {
  //   changeName(name: string) {
  //     this.name = name;
  //   },
  //   changeAge(age: number | string) {
  //     this.age = age;
  //   },
  // },
});
</script>

<style></style>
