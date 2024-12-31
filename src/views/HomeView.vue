<script setup>
import { computed, onMounted, ref } from 'vue';
import { useRouter } from 'vue-router';

const todos = ref([]);
const users = ref([]);
const textSearch = ref('');
const router = useRouter();

onMounted(()=>{
  (async()=>{
    const res = await fetch('https://jsonplaceholder.typicode.com/users')
    const data = await res.json();
    users.value = data
  })();
  // fetch('https://jsonplaceholder.typicode.com/todos')
  //     .then(response => response.json())
  //     .then(json => todos.value = json)
})
const filterTodos = computed(() => {
  return users.value.filter(item => item.name.toUpperCase().indexOf(textSearch.value.toUpperCase()) !== -1 );
})

</script>

<template>
  <main style="color: #080;padding: 2rem;">
    <input type="text" placeholder="Enter search here!" v-model="textSearch">
    <div class="group-card">
      <div class="card-item" v-for="user in filterTodos">
        <div @click="router.push({ path: `/user/${user?.id}`})">
          <h2>Name: {{ user?.name }}</h2>
          <i>Email: {{ user?.email }}</i>
        </div>
      </div>
      
    </div>
  </main>
</template>

<style>

</style>