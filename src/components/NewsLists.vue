<template>
    <div>
        <p>coco</p>
        <!-- <news-list :news="news"  v-for="newsItem in news" :key="newsItem.id"></news-list> -->
    </div>
</template>

<script>
import NewsSort from './NewsSort.vue';

export default {
    name: "news-lists",
    props: ["news"],
    data(){
        return {
            news: []
        }
    },
    components: {
        "news-list": NewsSort
    }
}
</script>

<style>

</style>