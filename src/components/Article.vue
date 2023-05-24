<template>
    <div class="container">
        <div class="card p-2 col-12 my-2" v-if="data.urlToImage">
            <div>
                <img class="img-fluid" :src="data.urlToImage" :alt="data.title">
            </div>
            <h4><a :href="data.url">{{ data.title }}</a></h4>
            <h6>{{ data.author }} | {{ data.source.name }}</h6>
            <p>
                {{ data.description }}
            </p>
        </div>
    </div>
    <div class="card p-2 row xl-col-4 sm-col-12 my-2" v-if="data.urlToImage === null">
        <div v-if="data.urlToImage">
            <img class="img-fluid" :src="data.urlToImage" :alt="data.title">
        </div>
        <h4><a :href="data.url">{{ data.title }}</a></h4>
        <h6>{{ data.author }} | {{ data.source.name }}</h6>
        <p>
            {{ data.description }}
        </p>
    </div>
</template>

<script>
    export default {
        props: ["data"],
    }
</script>

<style>

</style>