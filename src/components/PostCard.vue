<script>
export default {
    name: 'PostCard',
    data() {
        return {
            contentMaxLength: 200,
            baseUrl: "http://127.0.0.1:8000",
        }
    },
    props: {
        post: Object,
    },
    computed: {
        contentPreview() {
            if (this.post.content && this.post.content.length > this.contentMaxLength) {
                return this.post.content.substr(0, this.contentMaxLength) + '...';
            }
            return this.post.content;
        }
    },
    methods: {

    }
}
</script>

<template>
    <div class="card mb-3">
        <div class="card-body">
            <div class="row justify-content-between">
                <div class="col-4">
                    <img v-if="post.cover_image" class="w-100" :src="`${baseUrl}/storage/${post.cover_image}`" alt="">
                    <div v-else>
                        Nessuna immagine
                    </div>
                </div>
                <div class="col-7">
                    <h3 class="card-title">{{ post.title }}</h3>
                    <div class="d-flex justify-content-between">
                        <p>
                            <span v-for="tag in post.tags" :key="tag.id">#{{ tag.name }} </span>
                        </p>
                        <p class="text-end text-success">{{ post.category ? post.category.name : 'Nessuna Tecnologia' }}
                        </p>
                    </div>
                    <p class="card-text">
                        {{ contentPreview }}
                    </p>
                    <a class="btn btn-primary" href="">Leggi</a>
                </div>
            </div>

        </div>
    </div>
</template>