<template>
    <div v-for="thread in threads" :key="thread.id" class="col-large push-top">
        <h1>{{ thread.title }}</h1>
        <div class="post-list">
            <div v-for="postId in thread.posts" :key="postId" class="post">
                <div class="user-info">
                    <a href="#" class="user-name">{{ userById(postById(postId).userId).username }}</a>
                    <a href="#">
                        <img class="avatar-large" :src="userById(postById(postId).userId).avatar" alt="">
                    </a>
                    <p class="desktop-only text-small">107 posts</p>
                </div>
                <div class="post-content">
                    <div>
                        <p>{{ postById(postId).text }}</p>
                    </div>
                    <a href="#" style="margin-left: auto;" class="link-unstyled" title="Make a change"><i class="fa fa-pencil"></i></a>
                </div>
                <div class="post-date text-faded">
                    {{ postById(postId).publishedAt }}
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import sourceData from '../data.json'

    export default {
        data () {
            return {
                threads: sourceData.threads,
                posts: sourceData.posts,
                users: sourceData.users
            }
        },
        methods: {
            postById (postId) { return this.posts.find(post => post.id === postId) },
            userById (userId) { return this.users.find(user => user.id === userId) }
        }
    }
</script>

<style scoped>

</style>