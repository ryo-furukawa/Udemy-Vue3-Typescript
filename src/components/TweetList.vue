<script setup lang="ts">
import { defineProps } from 'vue'

type Tweet = {
    id: number,
    description: string,
}

type Props = {
    tweets: Tweet[]
}

defineProps<Props>()

const emit = defineEmits(['delete-tweet'])
const deleteTweet = (id: number) => {
    emit('delete-tweet', id)
}
</script>


<template>
    <li v-for="tweet in tweets" :key="tweet.id" class="tweet-list">
        <span>{{ tweet.description }}</span>
        <button class="delete-button" @click="deleteTweet(tweet.id)">delete</button>
    </li>
</template>

<style scoped>
.tweet-list {
    list-style: none;
    margin-bottom: 12px;
    border-radius: 4px;
    font-size: 12px;
    display: flex;
    justify-content: space-between;
    background-color: rgb(204, 219, 233);
    padding: 8px 20px;
    width: 300px;
}

.delete-button {
    color: #fff;
    font-weight: bold;
    background-color: #e64c2d;
    border-radius: 2px;
    border: none;
    width: 60px;
    height: 22px;
}

.delete-button:hover {
    background-color: #ef2f09;
}
</style>