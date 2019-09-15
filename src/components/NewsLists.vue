<template>
    <div>
        <!-- <ul> -->
            <!-- <button v-on:click="sortBy(newsItem.webPublicationDate)">date</button> -->
            <select v-model="currentOrder">
                <option value="lifeandstyle">Sort by life And Style</option>
                <option value="info">Sort by Info</option>
                <option value="money">Sort by Money</option>
                <option value="technology">Sort by Technology</option>
                <option value="society">Sort by Society</option>
                <option value="new-faces-of-tech">Sort by New Faces Of Tech</option>
            </select>
            <news-list-item v-for="newsItem in orderByKey(news, currentOrder)" :newsItem="newsItem" :key="newsItem.id"></news-list-item >
            <!-- <p>{{orderedItems(newsItem.webTitle)}}</p> -->
        <!-- </ul> -->
    </div>
</template>

<script>
import NewsListItem from './NewsListItem.vue';
import { eventBus } from '../main';

export default {
    name: "news-lists",
    data(){
        return {
            currentOrder: "info",
        }
    },
    props: ["news"],
    components: {
        "news-list-item": NewsListItem
    },
    methods: {
        // orderedItems(items) {
        //     items.sort(function(a, b){
        //     if (a < b) {return -1;}
        //     if (a > b) {return 1;}
        //     return 0;
        //     })
        //     return items
        // }
        // orderedItems(key) {
        //     return this.news.sort(function(a, b) {
        //     const x = a[key]; const y = b[key];
        //     return ((x < y) ? -1 : ((x > y) ? 1 : 0));
        //     });
        // }
        orderByKey(arr, key){
            return arr.filter(function(newsItem) {
                console.log(JSON.stringify(newsItem));
                console.log('ss',typeof(newsItem.sectionId))
                console.log('key',typeof(key))
                return newsItem.sectionId === key;
            })
        }
    }
}
</script>

<style>

</style>