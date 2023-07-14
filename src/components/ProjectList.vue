<script>
import axios from 'axios';

export default {
    data() {
        return {
            arrProjects: [],
        }
    },
    methods: {
        changePage(page) {
			this.currentPage = page;
			this.getProjects();
		},
		getProjects() {
			axios
				.get('http://localhost:8000/api/projects', {
					params: {
						page: this.currentPage,
					},
				})
				.then(response => {
					this.arrProjects = response.data.data;
					this.nPages = response.data.last_page;
				});
		},

    },
    created() {
        // richiesta dati al server
		axios
			.get('http://localhost:8000/api/projects', {
				params: {
					page: this.currentPage,
				},
			})
			.then(response => {
				this.arrProjects = response.data.data;
				this.nPages = response.data.last_page;
			});
    },

};
</script>

<template>
  <h2>i nostri progetti</h2>
  <ul>
    <li v-for="project in arrProjects" :key="project.id"><a href="">{{ project.title }}</a></li>
  </ul>

<nav>
  <ul class="pagination">
    <li class="page-item">
      <a class="page-link" href="#">Previous</a>
    </li>

    <li v-for="page in nPages" :key="page" class="page-item cursor-pointer" :class="{active: page == activePage}">
        <a class="page-link" href="#" @click="changePage(page)">{{ page }}</a>
    </li>
    
    <li class="page-item">
      <a class="page-link" href="#">Next</a>
    </li>
  </ul>
</nav>
  
</template>

<style scoped lang="scss">

</style>