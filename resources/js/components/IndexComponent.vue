<template>
    <div>
        <table class="table">
            <thead>
            <tr>
                <th scope="col">#</th>
                <th scope="col">Name</th>
                <th scope="col">Age</th>
                <th scope="col">Job</th>
                <th scope="col">Edit</th>
                <th scope="col">Delete</th>
            </tr>
            </thead>
            <tbody>
            <template v-for="person in people">
                <ShowComponent :person="person"></ShowComponent>
                <EditComponent :person="person"></EditComponent>

            </template>

            </tbody>
        </table>
    </div>
</template>

<script>
import ShowComponent from "./ShowComponent.vue";
import EditComponent from "./EditComponent.vue";
export default {
    name: "IndexComponent",
    components: {EditComponent, ShowComponent},
    data(){
        return {
            people: null,
            showEdit: false,
        }
    },
    methods:{
        getPeople(){
            axios.get('/api/people')
                .then(res => {
                    this.people = res.data
                })
        },



    },
    mounted() {
        this.getPeople()
    }


}
</script>

<style scoped>

</style>
