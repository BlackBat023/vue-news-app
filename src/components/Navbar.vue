<template>
    <div>
        <h1 class="bg-dark text-xl text-warning px-5 py-5">The<span class="text-danger">News</span>Hub</h1>
        <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
            <div class="container-fluid">
                <a class="navbar-brand" href="#">{{ subTitle }}</a>
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarNav">
                    <ul class="navbar-nav">
                        <li class="nav-item">
                            <button class="btn btn-dark" href="news" @click="changeNews(searchQ.news)">News</button>
                        </li>
                        <li class="nav-item">
                            <button class="btn btn-dark" href="sport" @click="changeNews(searchQ.sport)">Sport</button>
                        </li>
                        <li class="nav-item">
                            <button class="btn btn-dark" href="science" @click="changeNews(searchQ.science)">Science</button>
                        </li>
                        <li class="nav-item">
                            <button class="btn btn-dark" href="finance" @click="changeNews(searchQ.finance)">Fincance</button>
                        </li>
                    </ul>
                </div>
            </div>
            </nav>
    </div>
</template>

<script>
export default {
    data(){
        return {
            searchQ: {
                news: "news",
                sport: 'sport',
                science: 'science',
                finance: 'finance',
            },
            subTitle: 'NEWS',
        }
    },
    methods: {
        changeNews(value){
            this.subTitle = value.toUpperCase();
            this.$emit("newsChanged", value);
        },
    }
}
</script>

<style scoped>

</style>