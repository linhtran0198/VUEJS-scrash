<script setup>
import { useRoute } from 'vue-router';
import { onMounted, reactive, ref } from 'vue';
const router = useRoute();
const userData = reactive({
  email : '',
  name: '',
  phone: '',
  website: '',
});

const handleCreateNewUser = async() => {
    
}
</script>
<template>
    <main style="color: #000; padding: 2rem;">
       <h1 style="font-weight: bold;">Create User</h1>
       <div style="margin-bottom: 1rem;">
        <input type="text" placeholder="Enter Name" v-model="userData.name">
       </div>
       <div style="margin-bottom: 1rem;">
        <input type="text" placeholder="Enter Email" v-model="userData.email">
       </div>
       <div style="margin-bottom: 1rem;">
        <input type="text" placeholder="Enter Phone" v-model="userData.phone">
       </div>
       <div style="margin-bottom: 1rem;">
        <input type="text" placeholder="Enter Website" v-model="userData.website">
       </div>
       <div style="display: flex;" @click="handleCreateNewUser">
          <div class="btn-main" style="margin-top: 1rem; border-radius: 50px;">Create</div>
       </div>
    </main>
</template>