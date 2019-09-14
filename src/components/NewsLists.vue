<template>
    <div>
        <ul>
            <news-list-item v-for="newsItem in news" :newsItem="newsItem" :key="newsItem.id"></news-list-item >
        </ul>
    </div>
</template>

<script>
import NewsListItem from './NewsListItem.vue';

export default {
    name: "news-lists",
    props: ["news"],
    components: {
        "news-list-item": NewsListItem
    }
}
</script>

<style>

</style>