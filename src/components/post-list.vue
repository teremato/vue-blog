<template>
  <section class="post_list">
    <post-item
        v-for="post in posts"
        :key="post.id"
        :post="post"
    />
    <button
        class="btn"
        v-for="page in pages"
        :key="page"
        @click="nextPage(page)"
    >{{ page }}</button>
  </section>
</template>

<script>
import postItem from './post-item.vue'

export default {
    data() {
        return {
            posts: [],
            postNumber: 3,
            pages: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
        }
    },
    mounted() {
        this.getPost(this.postNumber)
       .then(data => this.posts = [...this.posts, ...data] )
    },
    watch: {
        postNumber() {
            this.getPost(this.postNumber)
            .then(data => this.posts = [...data])
        }
    },
    methods: {
        async getPost(page) {
            return fetch(`https://jsonplaceholder.typicode.com/posts?_page=${page}`)
            .then(response => response.json() )
            .then(data => data )
        },
        nextPage(page) {
            this.postNumber = page
        }
    },
    components: {
        ['post-item']: postItem,
    }
}
</script>

<style>
    .post_list {

        border-top: 5px solid rgb(255, 15, 83);
        margin-top: 30px;
        width: 80%;
    }
    .btn {
        cursor: pointer;
        margin: 10px;
        background: none;
        padding: 10px;
        border: none;
    }
</style>