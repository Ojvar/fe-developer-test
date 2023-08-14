<template>
    <div class="todo">
        <h5>{{ modelValue.title }}</h5>
        <div>Id: {{ modelValue.id }}</div>
        <div>User Id: {{ modelValue.user_id }}</div>
        <div>Status: {{ modelValue.user_id }} </div>
    </div>
</template>


<script setup lang="ts">
import { ITodo } from '../../models';

export interface IProps {
    modelValue: ITodo
}

defineProps<IProps>();
</script>

<style lang="scss" scoped>
.todo {
    text-align: left;
    padding: 0.0rem;
    margin-bottom: 2rem;
}
</style>