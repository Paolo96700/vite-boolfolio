<script>
import { store } from '../../store';

export default {
    data() {
        return {
            store,
        }
    },

    props: {
        project: {
            type: Object,
            required: true,
        }
    },

    methods: {
        getImageUrl(image) {
            return image
                ? this.store.baseUrl + 'storage/' + image : this.store.baseUrl + 'storage/default.jpg';
        }
    },
}
</script>


<template>
    <div class="col">
        <div class="card h-100">
            <div class="h-100">
                <!-- <img :src="'http://localhost:8000/storage/' + project.image" class="image img-fluid" alt=""> -->
                <img :src="getImageUrl(project.image)" class="image img-fluid" alt="">
            </div>

            <div class="card-body">
                <h5 class="card-title" style="font-weight: 700;">{{ project.title }}</h5>
                <p class="card-text">{{ project.description }}</p>
            </div>
            <ul class="list-group list-group-flush">
                <li class="list-group-item"><span style="font-weight: 700;">Author: </span> {{ project.author }}
                </li>
                <li class="list-group-item"><span style="font-weight: 700;">Creation Date: </span> {{
                    project.creation_date }}</li>
                <li class="list-group-item"><span style="font-weight: 700;">Last Update: </span>{{
                    project.last_update }}</li>
                <li class="list-group-item"><span style="font-weight: 700;">Collaborators: </span>{{
                    project.collaborators }}</li>
                <li class="list-group-item"><span style="font-weight: 700;">Technologies: </span>
                    <span v-for="technology in project.technologies" :key="technology.name">
                        {{ technology.name }},
                    </span>
                </li>
                <li class="list-group-item"><span style="font-weight: 700;">Type: </span>{{ project.type.name }}</li>
            </ul>
            <div class="card-body d-flex justify-content-between">
                <button type="button" class="btn btn-warning">
                    <a :href="project.link_github" class="card-link text-decoration-none">Link - Github</a>
                </button>
                <router-link :to="{ name: 'projects.show', params: { slug: project.slug } }"
                    class="btn btn-primary mt-auto">
                    View
                </router-link>

            </div>

        </div>
    </div>
</template>


<style lang="scss" scoped></style>