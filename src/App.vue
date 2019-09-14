<template>
  <div id="app">
    <h1>The Latest News of Javascript</h1>
    <h3>Powered by The Guardian</h3>
    <news-lists :news="newsList"></news-lists>
    <news-details :newsItem="selectedNewsItem"></news-details>
  </div>
</template>

<script>
  import NewsLists from './components/NewsLists.vue';
  import NewsDetails from './components/NewsDetails.vue';
  import { eventBus } from './main.js'

  export default {
    name: "app",
    data (){
      return {
        newsList: [],
        selectedNewsItem: null,
      }
    },
    mounted() {
        fetch(`https://content.guardianapis.com/search?q=javascript&format=json&api-key=test`)
        .then(res => res.json())
        .then(news => this.newsList = news.response.results)

        eventBus.$on('news-item-selected', (newsItem) => {
          this.selectedNewsItem = newsItem
        })
    },
    components: {
      "news-lists": NewsLists,
      "news-details": NewsDetails
    }
  }
</script>

<style>

</style>