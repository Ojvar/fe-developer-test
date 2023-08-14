<template>
    <div class="main-container">
        <h3>Latest Posts</h3>

        <div v-if="!hasPosts">
            <h5>No any Post registered</h5>
        </div>
        <div v-if="hasPosts" class="posts">
            <post-component class="post" v-for="post in postsList" :key="post.id" :model-value="post"></post-component>
        </div>
    </div>
</template>

<script setup lang="ts">
import { computed, onMounted, ref, Ref } from "vue"
import { Posts, PostsService } from "../../api"
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

<style lang="scss" scoped>
.main-container {
    text-align: left;
}

.posts {
    display: flex;
    justify-content: space-between;

    & .post {
        flex: 1 1 0px;
        border: 1px solid gray;
        border-radius: .4rem;
        padding: 1rem;
        margin: .5rem;
    }
}
</style>