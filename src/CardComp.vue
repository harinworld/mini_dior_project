<template>
    <div>
        <img :src="content.image" class="dior-img">
        <h4 @click="openFn">{{content.title}}</h4>
        <p>{{content.price}}원</p>
    </div>
</template>

<script>
export default {
    name:'CardComp',
    props:{
        content : Object,
    },
    methods:{
        openFn(){
            this.$emit('openModal', this.content.id)
        }
    }
    
}
</script>

<style lang="">
    
</style>