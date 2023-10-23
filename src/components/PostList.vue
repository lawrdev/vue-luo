<template>
  <div>
    <h2 style="font-size: 24px; font-weight: 700; letter-spacing: 1ch">Post list</h2>

    <div style="margin-block: 18px">
      <h3 style="padding-bottom: 12px; font-size: 20px; font-weight: 600">Create a post</h3>

      <form @submit.prevent="createPost">
        <div style="margin-bottom: 8px; display: flex; flex-direction: column; gap: 4px">
          <label for="post_title">Post Title</label>
          <input
            required
            type="text"
            name="post_title"
            v-model="createPostFormData.title"
            style="padding: 6px 24px; border-radius: 8px"
          />
        </div>

        <div style="margin-bottom: 8px; display: flex; flex-direction: column; gap: 4px">
          <label for="post_body">Post Body</label>
          <input
            ref="titleRef"
            required
            type="text"
            name="post_body"
            v-model="createPostFormData.body"
            style="padding: 6px 24px; border-radius: 8px"
          />
        </div>

        <div style="margin-bottom: 8px; display: flex; flex-direction: column; gap: 4px">
          <label for="post_user_id">User ID</label>
          <input
            type="number"
            name="post_user_id"
            v-model.number="createPostFormData.userId"
            style="padding: 6px 24px; border-radius: 8px"
          />
        </div>

        <button
          type="submit"
          style="
            text-transform: uppercase;
            margin-top: 30px;
            font-weight: 600;
            padding: 10px 20px;
            background-color: cornflowerblue;
          "
        >
          CREATE POST
        </button>
      </form>
    </div>

    <div style="margin-block: 20px">
      <h3 v-show="!!newPost" style="padding-bottom: 12px; font-size: 12px; font-weight: 600">
        {{ newPost?.id }} {{ newPost?.title }} by user-{{ newPost?.userId }}
      </h3>
      <p v-show="!!newPost" style="font-size: 19px">{{ newPost?.body }}</p>
    </div>

    <button
      style="
        margin-top: 30px;
        font-weight: 600;
        padding: 10px 20px;
        background-color: cornflowerblue;
      "
      @click="getPosts"
    >
      LOAD POST
    </button>

    <ul v-show="posts.length > 0">
      <div v-for="post in posts" :key="post.id">
        <h3 style="padding-bottom: 12px; font-size: 12px; font-weight: 600">
          {{ post.id }} {{ post.title }}
        </h3>
        <p style="font-size: 10px">{{ post.body }}</p>
      </div>
    </ul>
  </div>
</template>

<script setup lang="ts">
import axios from 'axios'
import type { PostType } from '@/util/types'
import { ref, onMounted, onBeforeMount } from 'vue'

interface PostProp {
  title: string
  body: string
  userId: number
}
interface PostReturnProp extends PostProp {
  id: number
}

const posts = ref<PostType[]>([])
const titleRef = ref(null)
const createPostFormData = ref<PostProp>({
  title: '',
  body: '',
  userId: 0
})
const newPost = ref<PostReturnProp>()

const getPosts = () => {
  console.log('FIREDDDDDD')
  axios.get(`https://jsonplaceholder.typicode.com/posts`).then((res) => {
    posts.value = res.data
  })
}

onBeforeMount(() => {
  console.log('we are hereeee!')
})

onMounted(() => {
  getPosts()
  if (titleRef.value) (titleRef.value as HTMLInputElement).focus()
})
const createPost = () => {
  axios
    .post(`https://jsonplaceholder.typicode.com/posts`, createPostFormData.value, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json; charset=UTF-8'
      }
    })
    .then((res) => (newPost.value = res.data))
}
</script>

<style scoped></style>
