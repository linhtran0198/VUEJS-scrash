<script setup>
import { useRoute } from 'vue-router';
import { onMounted, ref } from 'vue';
const router = useRoute();
const user = ref(null);
onMounted(()=>{
  (async()=>{
    const res = await fetch(`https://jsonplaceholder.typicode.com/users/${router.params.id}`)
    const data = await res.json();
    user.value = data
  })();
  // fetch('https://jsonplaceholder.typicode.com/todos')
  //     .then(response => response.json())
  //     .then(json => todos.value = json)
})
</script>
<template>
    <main style="color: #000; padding: 2rem;">
        <!-- Todo item {{ router.params.id }} -->
        
        <div class="card-item" >
            <h2>Name: {{ user?.name }}</h2>
            <i>UserName: {{user?.username  }}</i><br>
            <i>Email: {{user?.email  }}</i><br>
            <i>Phone: {{user?.phone  }}</i><br>
            <i>Website: {{user?.website  }}</i><br>
            <button >Delete</button>
        </div>
            
        
    </main>
</template>