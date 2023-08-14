<template>
  <div class="post">
    <h5>{{ modelValue.title }}</h5>
    <div>Id: {{ modelValue.id }}</div>
    <div>User Id: {{ modelValue.user_id }}</div>
    <p>Body: {{ modelValue.body }} </p>
  </div>
</template>


<script setup lang="ts">
import { IPost } from '../../models';

export interface IProps {
  modelValue: IPost
}

defineProps<IProps>();
</script>

<style lang="scss" scoped>
.post {
  text-align: left;
  padding: 0.0rem;
  margin-bottom: 2rem;
}
</style>