<template>
  <div class="menu">
    <a v-for="(a,i) in 메뉴들" :key="i">{{ a }}</a>
  </div>


  <Discount v-if="showDiscount == true" />

  <button @click="priceSort">가격순정렬</button>
  <button @click="priceBackSort">가격역순정렬</button>
  <button @click="titleSort">제목 순 정렬</button>
  <button @click="sortBack">되돌리기</button>
  
  <transition name="fade">
    <Modal @closeModal="모달창열렸니 = false"
    :원룸들="원룸들" :누른거="누른거" :모달창열렸니="모달창열렸니" />
  </transition>

  <Card @openModal="모달창열렸니 = true; 누른거 = $event" :원룸="원룸들[i]" v-for="(a,i) in 원룸들" :key="a"/>
  
  <!-- <Card :원룸="원룸들[1]" />
  <Card :원룸="원룸들[2]" />
  <Card :원룸="원룸들[3]" />
  <Card :원룸="원룸들[4]" />
  <Card :원룸="원룸들[5]" /> -->

</template>

<script>
import data from './assets/oneroom.js';
import Discount from './Discount.vue';
import Modal from './Modal.vue';
import Card from './Card.vue';

export default {
  name: 'App',
  data(){
    return {
      showDiscount : true,
      원룸들오리지널 : [...data],
      오브젝트 : { name : 'kim', age : 20},
      누른거 : 0,
      원룸들 : data,
      모달창열렸니 : false,
      신고수 : [0,0,0],
      메뉴들 : ['Home','Shop','About'],
      products : ['역삼동원룸','천호동원룸','마포구원룸'],
    }
  },
  methods: {
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
      this.원룸들.sort(function(a,b){
        return a.price - b.price
      })
    },

    priceBackSort(){
      this.원룸들.sort(function(a,b){
        return b.price - a.price
      })
    },
    titleSort(){
      this.원룸들.sort(function(a, b){
        return a.title.localeCompare(b.title);
      })
    },
    sortBack(){
      this.원룸들 = [...this.원룸들오리지널];
    }
  },

  mounted(){
    
  },

  components: {
    Discount : Discount,
    Modal : Modal,
    Card : Card,
  }
}
</script>

<style>
body {
  margin : 0
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 60%; height: 60%;
  background: rgba(0, 0, 0, 5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
.room-img {
  width: 50%;
  margin-top: 40px;
}
.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
.start {
  opacity: 0;
  transition: all 1s;
}
.end {
  opacity: 1;
}
.fade-leave-to {
  opacity: 0;
}
.fade-enter-from {
  transform: translateY(-1000px);
  opacity: 0;
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  transform: translateY(0px);
  opacity: 1;
}
.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  opacity: 0;
}

</style>
