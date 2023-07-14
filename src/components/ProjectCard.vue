<script>
import axios from 'axios';

export default {
    data() {
        return {
            arrProjects: [],
        }
    },
    
    created() {
        // richiesta dati al server
		axios.get('http://localhost:8000/api/projects')
		.then(response => this.arrProjects = response.data.data);
    },

};
</script>

<template>
  
</template>

<style lang="sass" scoped>

</style>