<template>

  <transition name="fade">
    <ModalRead :room="room" :number="number" :modal_open="modal_open" @modalClose="modal_open = false"/>
  </transition>
  

  

  <div class="menu">
    <a href="#" v-for="(item,k) in list" :key="k">{{ item }}</a>
  </div>

  <Discount v-if="showDiscount == true " />

  <button class="btn-price" @click="priceSort">가격순정렬</button>
  <button class="btn-price-revers" @click="priceRverseSort">가격역순정렬</button>
  <!-- <button @click="priceKorea">가나다순정렬</button> -->
  <button class="btn-back" @click="sortBack">되돌리기</button>
  <!-- 가격높은순정렬 -->
  <!-- 상품명 가나다순정렬 -->

  <Card  @openModal="modal_open = true; number = $event " :room="room[index]" 
        v-for="(item, index) in room" :key="item"
  />

  <!-- <Card :room="room[1]" />
  <Card :room="room[2]" />
  <Card :room="room[3]" />
  <Card :room="room[4]" />
  <Card :room="room[5]" /> -->

</template>

<script>
import RoomData from '@/oneroom.js';
import Discount from '@/components/Discount.vue';
import ModalRead from '@/components/ModalRead.vue';
import RoomList from '@/components/RoomList.vue';


export default {
  name: 'App',

  data() {
    
    return {
      showDiscount : true,
      오브젝트 : {
        name : 'kim',
        age : 20
      },
      roomOrigin : [...RoomData],
      number: 0,
      room : RoomData,
      modal_open : false,
      신고수: [0, 0, 0, 0, 0, 0],
      style_b: 'color: #2c3e50',
      list: ['Home', 'Shop', 'about'],
      products: ['역삼동원룸', '천호동원룸', '마포구원룸'],
      price: [50, 60, 70],
    }
  },
  methods: {
    increase (){
      this.신고수 += 1;
    },
    priceSort() {
      this.room.sort(function(a, b){
        return a.price - b.price
      })
    },
    sortBack(){
      this.room = [...this.roomOrigin];
    },
    priceRverseSort() {
      this.room.sort(function(a, b){
        return b.price - a.price
      })
    },
    priceKorea() {
      this.room.sort();
    }
    
  },

  components: {
      Discount : Discount,
      ModalRead : ModalRead,
      Card : RoomList
  }
}
</script>

<style>

body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}


#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  opacity: 0;
  transform: translateY(1000px);
}

.fade-enter-from {
  opacity: 0;
  transform: translateY(-1000px);
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  opacity: 1;
  transform: translateY(0px);
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

button {
  margin: 10px 10px 20px;
  background: conic-gradient(from 45deg, #5ad85a, #bdf5b8);
  border: 0;
  padding: 3px 10px;
  color: #000;
  font-weight: bold;
  border-radius: 10px;
  cursor: pointer;
}

button:hover {
  background: wheat;
}

</style>
