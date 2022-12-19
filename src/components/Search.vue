<template>
    <div class="col-2">
        <input type="text" placeholder="SEARCH" v-model="searchQ">
        <button class="btn btn-primary" @click="changeNews">Submit</button>
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