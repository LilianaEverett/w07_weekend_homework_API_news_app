<template>
  <div id="app">
    <p>app container</p>
    <news-lists :news="newsLists"></news-lists>
        <!-- <news-Lists >hggygi</news-Lists> -->

    <!-- <news-details :newsItem="newsItemSelected"></news-detail> -->
  </div>
</template>

<script>
  import NewsLists from './components/NewsLists.vue';
  // import NewsDetails from './components/NewsDetails.vue';

  export default {
    // name: "app",
    data (){
      return {
        newsLists: [],
        newsItemSelected: {},
      }
    },
    components: {
      "news-lists": NewsLists,
      // "news-details":NewsDetails
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