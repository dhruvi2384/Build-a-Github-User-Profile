<script setup lang="ts">
import axios from "axios";
import { onMounted, ref } from "vue";
import { useRoute } from "vue-router";

// data
const userProfile = ref();
const route = useRoute()

// method
async function getUserdata() {
  const userData = await axios.get(`https://api.github.com/users/${route.query.myid}`);
  userProfile.value = userData.data;
}

// hooks
onMounted(() => {
  getUserdata();
  console.log(route.query.myid,'router');
});
</script>

<template>
    <div class="container">
        <div class="main_img">
            <img src="../assets/Image/9334389.jpg" alt="user">
            <p>Followers : </p>
            <p>Following : </p>
        </div>
    </div>
</template>