<template>
    <div class="discount">
        <h4>지금 결제하면 {{amount}}% 할인</h4>
    </div>
</template>

<script>
export default {
    name: 'DiscountComp',
    data(){
        return{
            amount : 30,
            intervalId : null
        }
    },
    mounted(){
        this.intervalId = setInterval(()=>{
            if(this.amount <= 0){
                clearInterval(this.intervalId);
            }else{
                this.amount--;
            }
        },1000);
    }
}
</script>


