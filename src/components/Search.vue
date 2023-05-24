<template>
    <div class="col-12">
        <input type="text" placeholder="SEARCH" v-model="searchQ">
        <button class="mx-2 btn btn-dark" @click="changeNews">Submit</button>
    </div>
</template>

<script>
export default {
    data(){
        return {
            searchQ: '',
        }
    },
    methods: {
        changeNews(){
            this.$emit("newsChanged", this.searchQ);
            this.searchQ = '';
        }
    }
}
</script>