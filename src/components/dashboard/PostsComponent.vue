<template>
    <div class="mb-5">
        <h3 class="text-start">My Todo's</h3>

        <div v-if="!hasPosts">
            <h5>No any Todo registered</h5>
        </div>
        <div v-if="hasPosts" class="row justify-content-center">
            <post-component class="col-12 m-2" v-for="post in postsList" :key="post.id"
                :model-value="post"></post-component>
        </div>
    </div>
</template>

<script setup lang="ts">
import { computed, onMounted, ref, Ref } from "vue"
import { PostsService, Posts } from "../../api"
import PostComponent from "./PostComponent.vue"

// Services
const postsService = new PostsService();

// Refs
const postsList: Ref<Posts> = ref([]);

// Computed
const hasPosts = computed(() => postsList.value.length !== 0)

// Functions
const loadPostsList = async () => {
    const list = await postsService.loadPosts();
    postsList.value = list.sort((a, b) => b.id - a.id);
}

// Hooks
onMounted(() => {
    loadPostsList();
})
</script>


    