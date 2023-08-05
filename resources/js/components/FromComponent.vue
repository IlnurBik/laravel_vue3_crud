<template>
    <div class="w-25 mt-1">
        <input class="form-control" v-model="name" placeholder="name">
    </div>
    <div class="w-25 mt-1">
        <input class="form-control" v-model="age" placeholder="age">
    </div>
    <div class="w-25 mt-1">
        <input class="form-control" v-model="job" placeholder="job">
    </div>
    <div class="w-25 mt-1">
        <input type="submit" :disabled="!isDisabled" @click.prevent="addPerson" class="btn btn-primary"
               value="Добавить">
    </div>
    <div>
        <div> Color: {{ color }}</div>
    </div>
</template>

<script>
export default {
    name: "FromComponent",
    data(){
        return {
            name: null,
            age: null,
            job: null,
        }
    },
    props:{
      color:{
          required: true
      }
    },
    methods:{
        addPerson(){
            axios.post('api/people', {name: this.name, age: this.age, job: this.job})
                .then( res => {
                    this.$parent.$refs.index.getPeople()
                    this.name = null;
                    this.age = null;
                    this.job = null;
                })
        },
    },
    computed:{
        isDisabled(){
            return this.name && this.age && this.job;
        }
    }
}
</script>

<style scoped>

</style>
