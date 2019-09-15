<template>
    <div class="item-detail">
        <h2 v-if="newsItem">{{newsItem.webTitle}}</h2>
        <p v-if="newsItem">Publication Date: {{newsItem.webPublicationDate}}</p>
        <p v-if="newsItem">Section: {{newsItem.sectionName}}</p>
        <a v-if="newsItem" v-bind:href="newsItem.webUrl" target="_blank">Read Article</a>
    </div>
</template>

<script>
export default {
    name: "news-details",
    props: ['newsItem']

}
</script>

<style>
.item-detail {
    margin: 40px;
}
</style>