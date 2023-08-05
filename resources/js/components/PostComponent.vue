<template>
<div class="app">
<FromComponent :color="color"></FromComponent>
<IndexComponent ref="index"></IndexComponent>

</div>
</template>

<script>
import FromComponent from "./FromComponent.vue";
import IndexComponent from "./IndexComponent.vue";
export default {
    name: "PostComponent",
    components: {IndexComponent, FromComponent},
    data(){
        return{
            color: 'green',
        }
    }
}
</script>

<style>
.app{
    padding: 15px;
}
</style>
