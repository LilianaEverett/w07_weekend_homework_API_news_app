<template>
  <div id="app">
    <p>app container</p>
    <news-Lists :news="newsList"/>
        <news-Lists >hggygi</news-Lists>

    <!-- <news-detail :newsItem="newsItemSelected"></news-detail> -->
  </div>
</template>

<script>
  import NewsLists from './components/NewsLists.vue';
  import NewsDetails from './components/NewsDetails.vue';

  export default {
    name: "app",
    components: {
      "news-lists": NewsLists,
      "news-detail":NewsDetails
    },
    data (){
      return {
        newsList: [],
        newsItemSelected: {},
      }
    },
    mounted() {
        fetch(`https://content.guardianapis.com/search?q=javascript&format=json&api-key=test`)
        .then(res => res.json())
        .then(news => this.news = news)
    }
  }
</script>

<style>

</style>