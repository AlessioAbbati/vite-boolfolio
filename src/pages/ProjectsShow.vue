<script>
import { store } from '../store';
import axios from 'axios';
// import { DateTime } from "luxon";

export default {
    data() {
        return {
            store,
            // luxon: DateTime,
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

<template v-if="project">
  <h1>{{ project.title }}</h1>
  <!-- <span>{{ project.last_update }}</span> -->
  <img :src="this.store.baseUrl + 'storage/' + project.image" class="card-img-top" :alt="project.id">
  <!-- <img :src="this.store.getImageUrl(project.image)" class="card-img-top" :alt="project.id"> -->

</template>

<style scoped lang="scss">

</style>

