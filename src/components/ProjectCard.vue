<script>
// import axios from 'axios';

export default {
    props: {
        title: {
            type: String,
            required: true
        },
        description: {
            type: String,
            required: true
        },
        image: {
            type: String,
            required: true
        },
        id: {
            type:String,
            required: true
        }
  }
};
</script>

<template>
    <div class="card" style="width: 18rem;">
        <img :src="image" class="card-img-top" :alt="id">
        <div class="card-body">
            <h5 class="card-title">{{ title }}</h5>
            <p class="card-text">{{ description }}</p>
        </div>
    </div>
</template>

<style lang="sass" scoped>

</style>