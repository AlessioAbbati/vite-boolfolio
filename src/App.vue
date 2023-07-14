<script>
import ProjectList from './components/ProjectList.vue'
import ProjectCard from './components/ProjectCard.vue'

export default {
    components: {
        ProjectList,
        ProjectCard,
    }

}

</script>

<template>
  <h1>boolpress</h1>
  <project-list />
  <project-card />
</template>

<style lang="scss">
@import "bootstrap/scss/bootstrap";
</style>
