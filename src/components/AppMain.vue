<script>
import axios from 'axios';
import AppLoader from './AppLoader.vue';
import PostCard from './PostCard.vue';
export default {
    name: "AppMain",
    components: { PostCard, AppLoader },
    data() {
        return {
            baseUrl: "http://localhost:8000",
            posts: [],
            loading: false
        };
    },
    created() {
        this.getPosts();
    },
    methods: {
        getPosts() {
            this.loading = true;
            axios.get(`${this.baseUrl}/api/posts`).then(resp => {
                this.posts = resp.data.results;
                this.loading = false;
            });
        }
    },
}
</script>

<template>
    <div class="container">
        <h2 class="text-center mb-3">Tutti i nostri post</h2>
        <AppLoader v-if="loading" />
        <div v-else class="row justify-content-center">
            <div class="col-11 col-md-10 col-lg-8">
                <PostCard :post="post" v-for="post in posts" :key="post.id" />
            </div>
        </div>
    </div>
</template>