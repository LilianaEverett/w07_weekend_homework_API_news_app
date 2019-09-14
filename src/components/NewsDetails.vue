<template>
    <div>
        <ul>
            <li v-if="newsItem">{{newsItem.webTitle}}</li>
            <li v-if="newsItem">{{newsItem.webPublicationDate}}</li>
            <a v-if="newsItem" href="newsItem.webUrl">Read More</a>
        </ul>
    </div>
</template>

<script>
export default {
    name: "news-details",
    props: ['newsItem']

}
</script>

<style>

</style>