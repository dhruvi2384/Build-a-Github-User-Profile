<script setup lang="ts">
const props = defineProps({
  userCardDetail: Object,
});

const created = props.userCardDetail.created_at.slice(0,4)

</script>

<template>
  <ul>
    <li>
      <div class="card">
        <div class="user_profile">
          <img :src="props.userCardDetail.avatar_url" alt="user-image" />
        </div>
        <h1>{{ props.userCardDetail.name }}</h1>
        <p class="date_of_join">Joined : {{created}} </p>
      </div>
      <div class="follower">
        <p class="date_of_join">{{props.userCardDetail.following}}</p>
        <div class="flex_display">
          <img src="../assets/Image/portrait.svg" alt="user" />
          <span>{{props.userCardDetail.followers}}</span>
        </div>
      </div>
    </li>
  </ul>
</template>

<style scoped></style>
