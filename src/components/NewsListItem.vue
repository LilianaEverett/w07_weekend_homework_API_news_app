<template>
    <div class="list-item">
        <ul>
            <li v-on:click="handleClick">{{newsItem.webTitle}}</li>
        </ul>
    </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
    name: 'news-list-sort',
    props: ['newsItem'],
    methods: {
        handleClick() {
            eventBus.$emit('news-item-selected', this.newsItem)
        }
    }
}
</script>

<style>
li {
    font-family: Arial, Helvetica, sans-serif;
    padding: 10px;
    border: ridge olivedrab;
}

ul{
    list-style-type: none;
}
</style>