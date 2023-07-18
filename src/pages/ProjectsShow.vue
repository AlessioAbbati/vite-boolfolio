<script>
import { router } from '../router';
import { store } from '../store';
import axios from 'axios';
import { DateTime } from "luxon";

export default {
    data() {
        return {
            store,
            luxon: DateTime,
            project: {},
        }
    },
    created() {
        // fai la richiesta axios
        axios.get(this.store.baseUrl + 'api/projects/' + this.$route.params.slug)
        .then(response => {
            if (response.data.success) {
                this.project = response.data.results;
            } else {
                this.$router.push({ name: 'page404' });
            }
        });

        
        console.log(this.project);
    },


};
</script>

<template v-if="project">
  <h1>{{ project.title }}</h1>
  <span>Last update: {{ project.last_update }}</span> <br>
  <span> {{ this.luxon.now().toFormat('dd/MM/yyyy') }}</span>
  <img :src="this.store.baseUrl + 'storage/' + project.image" class="card-img-top" :alt="project.id">
  <!-- <img :src="this.store.getImageUrl(project.image)" class="card-img-top" :alt="project.id"> -->

</template>

<style scoped lang="scss">

</style>

