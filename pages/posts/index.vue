<template lang="">
    <div>
        <h2> Make API Request - the Vue Way </h2>
        <div class="container row">
            <Card v-for="(post, index) in posts" :key="post.id" :post="post" class="ml-auto mr-auto" />
            <button class="btn btn-danger" v-scroll-to="'body'"> Back to Top </button>
        </div>
    </div>
</template>
<script>
import Card from '@/components/Card'
import axios from 'axios'

export default {
    components: {
        Card
    },
    data() {
        return {
            allPosts: ''
        }
    },
    computed: {
        posts() {
            return this.$store.getters.posts
        }
    },
    async fetch({store}) { // asyncData
        let {data} = await axios.get('https://jsonplaceholder.typicode.com/posts')
        store.dispatch('setPosts', data)
    },
    head: {
        title: 'List of Post'
    }
}
</script>

<style lang="">

</style>