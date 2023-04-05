<template lang="">
    <div class="black-bg" v-if="modal == true">
        <div class="white-bg">
            <h4>{{contents[select].title}}</h4>
            <img :src="contents[select].image">
            <p>{{contents[select].content}}</p>
            <input v-model.number="month">
            <p> {{month}}개 : {{contents[select].price * month}}원</p>
            <button @click="$emit('closeModal')">닫기</button>
        </div>
    </div>
</template>

<script>

export default {
    name:'ModalComp',
    data(){
        return{
            month : 1,
        }
    },
    watch:{
        month(a){
            if(a>5){
                alert('5개 이상 구매 불가')
            }
            if(isNaN(a) == true){
                alert('숫자만 입력할 수 있습니다.');
                this.month = 1;
            }
        }
    },
    props:{
        contents : Array,
        select : Number,
        modal : Boolean,
    },
    
    components: {
    
  }
}
</script>

<style>
    .white-bg img{
        width: 80vw;
    }
</style>