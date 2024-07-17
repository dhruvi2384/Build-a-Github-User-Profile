<script setup lang="ts">
import UserProfile from "../components/UserProfileCard.vue";
import axios from "axios";
import {  ref } from "vue";

// data
const userProfile = ref();
const userName = ref()

// method
async function getUserdata() {
  const userData = await axios.get(`https://api.github.com/users/${userName.value}`);
  console.log('userData: ', userData);
  userProfile.value = userData.data;
}

// hooks

</script>

<template>
  <main>
    <div class="container">
      <h1 class="title">GitHUB USER PROFILE</h1>
      <input type="text" v-model="userName" />
      <button @click="getUserdata()" >Search</button>

      <div class="flex_display">
        <UserProfile
          :userCardDetail="userProfile"
        />
      </div>
    </div>
  </main>
</template>
