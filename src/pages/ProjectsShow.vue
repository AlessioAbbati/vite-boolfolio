<script>
import {store } from '../store';

export default {
    data() {
        return {
            store,
        }
    },
    created() {
        // fai la richiesta axios
        axios.get(this.store.baseUrl + 'projects/projects/' + this.$route.params.slug)
        .then(response => response.data.data)
    }

};
</script>

<template>
  <h2>show</h2>
</template>

<style>

</style>

