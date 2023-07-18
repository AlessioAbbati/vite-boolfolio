<script>
import {store } from '../store';
import axios from 'axios';

export default {
    data() {
        return {
            store,
            project: {},
        }
    },
    created() {
        // fai la richiesta axios
        axios.get(this.store.baseUrl + 'api/projects/' + this.$route.params.slug)
        .then(response => this.project = response.data.results)
        console.log(this.project);
    },
    

};
</script>

<template>
  <h1>{{ project.title }}</h1>
  <img :src="this.store.baseUrl + 'storage/' + project.image" class="card-img-top" :alt="project.id">
  <!-- <img :src="this.store.getImageUrl(project.image)" class="card-img-top" :alt="project.id"> -->
  
</template>

<style scoped lang="scss">

</style>

