<template>
  <div id="app">
    <div class="header">
      <h1>The Latest News of Javascript</h1>
      <h3>Powered by The Guardian</h3>
    </div>
    <news-details v-bind:newsItem="selectedNewsItem"></news-details>
    <div class="news-lists">
      <news-list v-bind:news="newsList"></news-list>
      <news-list-sort v-bind:news="newsList"></news-list-sort>
    </div>
  </div>
</template>

<script>
  import NewsListSort from './components/NewsListSort.vue';
  import NewsDetails from './components/NewsDetails.vue';
  import NewsList from './components/NewsList.vue';
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
      "news-list": NewsList,
      "news-list-sort": NewsListSort,
      "news-details": NewsDetails
    }
  }
</script>

<style>
#app {
  font-family: Georgia, serif;
  text-decoration: none;
}
.news-lists {
  display: flex;
}

h1 {
  text-align: center;
}

h3 {
  text-align: center;
}

.header {
  padding: 20px;
  background-color: olivedrab;
}

</style>