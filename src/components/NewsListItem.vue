<template>
    <div>
        <li v-on:click="handleClick">{{newsItem.webTitle}}</li>
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

</style>