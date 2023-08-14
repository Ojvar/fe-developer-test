<template>
  <h1>My Dashboard</h1>
  <todos-component></todos-component>
  <posts-component></posts-component>
</template>

<script setup lang="ts">
import TodosComponent from "./dashboard/TodosComponent.vue";
import PostsComponent from "./dashboard/PostsComponent.vue";
</script>

<style scoped></style>
