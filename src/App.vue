<template>
  <div class="app">
    <header>
      <div class="title">
        <img src="./assets/1.png" alt="Kanami Etou">
        <h1>Mahathirtama Ahmad</h1>
      </div>
      <div class="order">
        <button @click="handleSubmit('title')" >Order By Title</button>
        <button @click="handleSubmit('salary')" >Order By Salary</button>
        <button @click="handleSubmit('location')" >Order By Location</button>
      </div>
    </header>
    <jobs-list :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs, ref } from "vue";
import Job from "./types/job";
import JobsList from "./components/JobsList.vue"
import OrderTerm from "./types/OrderTerm"
export default defineComponent({
  name: "App",
  components: {
    JobsList
  },
  setup() {
    // const state = reactive({
    //   name: 'tama',
    //   data: ''
    // })
    // return {...toRefs(state)}

    // const name = ref('tama')
    // const data = ref('')
    // return {name, data}

    const jobs = ref<Job[]>([
      { title: "tama", location: "Depok", salary: 1000, id: "1" },
      { title: "Data", location: "palsigunung", salary: 100, id: "2" },
      { title: "zeta", location: "Inodnesia", salary: 9000, id: "3" },
      { title: "kobo", location: "jakarta", salary: 6000, id: "4" },
      { title: "kaela", location: "Isekai", salary: 1000, id: "5" },

    ]);

    const order = ref<OrderTerm>('title')

     const handleSubmit = (term: OrderTerm) => {
        order.value = term
      }
    return {jobs, handleSubmit, order}
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
  color: blue;
  border: 3px solid blueviolet;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}

header .title {
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
