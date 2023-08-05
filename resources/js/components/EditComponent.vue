<template>
    <tr v-if="$parent.showEdit === person.id && person">
        <th scope="row">{{ person.id }}</th>
        <td><input class="form-control" v-model="person.name"></td>
        <td><input class="form-control" v-model="person.age"></td>
        <td><input class="form-control" v-model="person.job"></td>
        <td><button :disabled="!isDisabled" @click="update(person.id, person.name, person.age, person.job)"
                    class="btn btn-primary">Update
        </button></td>
    </tr>
</template>

<script>
export default {
    name: "EditComponent",
    props: {
      person:{
          required: true
      }
    },
    methods:{
        update(id, name, age, job){
            axios.patch(`/api/people/${id}`, {name: name, age: age, job: job})
                .then( res => {
                    console.log(res.data);
                    this.$parent.showEdit = null;
                })
        },
    },
    computed:{
        isDisabled(){
            return this.person.name && this.person.age && this.person.job;
        }
    }
}
</script>

<style scoped>

</style>
