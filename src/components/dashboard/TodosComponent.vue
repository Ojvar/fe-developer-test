<template>
    <div class="main-container">
        <h3>My Todo's</h3>

        <div v-if="!hasTodos">
            <h5>No any Todo registered</h5>
        </div>
        <div v-if="hasTodos" class="todos">
            <todo-component class="todo" v-for="todo in todosList" :key="todo.id" :model-value="todo"></todo-component>
        </div>
    </div>
</template>

<script setup lang="ts">
import { computed, onMounted, ref, Ref } from "vue"
import { TodosService, Todos } from "../../api"
import TodoComponent from "./TodoComponent.vue"

// Services
const todosService = new TodosService();

// Refs
const todosList: Ref<Todos> = ref([]);

// Computed
const hasTodos = computed(() => todosList.value.length !== 0)

// Functions
const loadTodosList = async () => {
    todosList.value = await todosService.loadTodos();
}

// Hooks
onMounted(() => {
    loadTodosList();
})
</script>

<style lang="scss" scoped>
.main-container {
    text-align: left;
}

.todos {
    display: flex;
    justify-content: space-between;

    & .todo {
        flex: 1 1 0px;
        border: 1px solid gray;
        border-radius: .4rem;
        padding: 1rem;
        margin: .5rem;
    }
}
</style>