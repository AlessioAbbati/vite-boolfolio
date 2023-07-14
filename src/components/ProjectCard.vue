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
    // data() {
    //     return {
    //         arrProjects: [],
    //     }
    // },
    // created() {
    //     // richiesta dati al server
	// 	axios.get('http://localhost:8000/api/projects')
	// 	.then(response => this.arrProjects = response.data.data);
    // },

};
</script>

<template>
    <div v-for="project in arrProjects" :key="project.id" class="card" style="width: 18rem;">
        <img :src="project.image" class="card-img-top" :alt="project.id">
        <div class="card-body">
            <h5 class="card-title">{{ project.title }}</h5>
            <p class="card-text">{{ project.description }}</p>
        </div>
    </div>

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

<style lang="sass" scoped>

</style>