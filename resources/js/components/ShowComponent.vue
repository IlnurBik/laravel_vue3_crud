<template>
    <tr v-if="$parent.showEdit !== person.id">
        <th scope="row">{{ person.id }}</th>
        <td>{{ person.name }}</td>
        <td>{{ person.age }}</td>
        <td>{{ person.job }}</td>
        <td><button @click="edit(person.id)" class="btn btn-primary">Edit</button></td>
        <td><button @click="deletePerson(person.id)" class="btn btn-danger">Delete</button></td>
    </tr>
</template>

<script>
export default {
    name: "ShowComponent",
    props:{
        person:{
            required: true,
        }
    },
    methods: {
        edit(id){
            this.$parent.showEdit = id;
        },
        deletePerson(id){
            axios.delete(`/api/people/${id}`)
                .then( res => {
                    console.log(res.data)
                    this.$parent.getPeople()
                })
        }
    }
}
</script>

<style scoped>

</style>
