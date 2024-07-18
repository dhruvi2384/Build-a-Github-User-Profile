<script setup lang="ts">
import UserProfile from "../components/UserProfileCard.vue";
import axios from "axios";
import { ref, watch } from "vue";

// data
const userProfile = ref();
const userName = ref();

// method
async function getUserdata() {
  const userData = await axios.get(
    `https://api.github.com/users/${userName.value}`
  );
  console.log("userData: ", userData);
  userProfile.value = userData.data;
}
watch(userName, async (newValue) => {
  try {
    const userData = await axios.get(
      `https://api.github.com/users/${newValue}`
    );
    userProfile.value = userData.data;
  } catch (error) {
    console.log("API limit done",error);
  }
});
</script>

<template>
  <main>
    <div class="container">
      <h1 class="title">GitHUB USER PROFILE</h1>
      <div class="serching_sec">
        <input type="text" v-model="userName" />
        <button @click="getUserdata()">Search</button>
      </div>

      <div class="flex_display mt-3" v-if="userProfile">
        <UserProfile :userCardDetail="userProfile" />
      </div>
    </div>
  </main>
</template>
