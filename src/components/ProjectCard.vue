<script>
import axios from 'axios';
export default {
    name: 'ProjectCard',
    data() {
        return {
            projects: []
        };
    },
    methods: {
        getProjects() {
            axios.get('http://127.0.0.1:8000/api/projects')
                .then((response) => {
                this.projects = response.data.results
            })
        }
    },
    mounted() {
        this.getProjects();
    }
}
</script>

<template>
<h1 class="text-center">I miei progetti</h1>
<div class="container">
    <div class="row">
        <div v-for="project in projects" class="col-4">
            <div class="card">
                <div class="card-body">
                    <h5 class="card-title">{{project.title}}</h5>
                    <small>{{project.slug}}</small>
                    <p class="card-text">{{project.summary}}</p>
                </div>
            </div>
        </div>
    </div>
</div>
</template>

<style  scoped lang="scss">


</style>
