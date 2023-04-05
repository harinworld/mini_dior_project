<template>

  <transition name="fade">
    <ModalComp @closeModal="modal = false;"  :contents="contents" :select="select" :modal="modal"/>
  </transition>

  <div class="menu">
    <a v-for="a in 매뉴들" :key="a">{{a}}</a>
  </div>

  <DiscountComp/>

  <button @click="priceSort">가격순정렬</button>
  <button @click="pricebackSort">가격역순정렬</button>
  <button @click="abcSort">가나다순정렬</button>
  <button @click="sortBack">원래대로</button>

  <CardComp 
    @openModal="modal = true; select = $event"
    :content="contents[i]" v-for="(a,i) in contents" :key="a"/>

</template>

<script>
import data from './data';
import ModalComp from './ModalComp.vue';
import CardComp from './CardComp.vue';
import DiscountComp from './DiscountComp.vue';



export default {
  name: 'App',
  data(){
    return{
      showDiscount : true,
      original : [...data],
      select : 0,
      contents : data,
      modal : false,
      신고수 : [0,0,0],
      매뉴들 : ['Home', 'Shop', 'About'],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
    }
  },
  methods : {
    increase(){
      this.신고수[0] += 1;
    },
    increase2(){
      this.신고수[1] += 1;
    },
    increase3(){
      this.신고수[2] += 1;
    },
    priceSort(){
      this.contents.sort(function(a,b){
        return a.price - b.price
      })
    },
    pricebackSort(){
      this.contents.sort(function(a,b){
        return b.price - a.price
      })
    },
    abcSort(){
      this.contents.sort(function(a,b){
        var titleA = a.title.toUpperCase();
        var titleB = b.title.toUpperCase();
        if(titleA < titleB){
          return -1;
        }
        if(titleA > titleB){
          return 1;
        }
        return 0;
      })
    },
    sortBack(){
      this.contents = [...this.original];
    }
  },
  mounted(){
    // setTimeout(()=>{
    //   this.showDiscount = false;
    // }, 2000)
    // setInterval(()=>{
    //   this.showDiscount = false;
    // }, 1000)
  },

  components: {
    ModalComp,
    CardComp,
    DiscountComp,
  }
}
</script>

<style>
.fade-leave-from{opacity: 1;}
.fade-leave-active{transition: all 1s;}
.fade-leave-to{opacity: 0;}

.fade-enter-from{
  transform: translateY(-1000px);
}
.fade-enter-active{transition: all 0.8s;}
.fade-enter-to{transform: translateY(0px);}

body{
  margin: 0;
}
div{
  box-sizing: border-box;
}
.discount{
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
.black-bg{
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed;
  padding: 20px;
}
.white-bg{
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}
.dior-img{
  width: 100%;
  margin-top: 40px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu{
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a{
  color: white;
  padding: 10px;
}
</style>
