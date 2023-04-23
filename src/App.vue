<template>

  <!-- <div class = 'black-bg' v-if = 'modalOpen == true'>
    <div class = 'white-bg'>
      <h4>{{onerooms[modalPressed].title}}</h4>
      <img :src="onerooms[modalPressed].image" style = "width: 100%">
      <p>{{onerooms[modalPressed].content}}</p>
      <p>{{onerooms[modalPressed].price}}원</p>
      <button @click = 'modalOpen = false'>닫기</button>
    </div>
  </div> -->
  <Transition name = "fade">
    <ModalComponent @closeModal = 'modalOpen = false'
    :onerooms = 'onerooms' :modalPressed = 'modalPressed' :modalOpen = 'modalOpen' :oneroomsOriginal = 'oneroomsOriginal'/>
  </Transition>
  

  <!-- v-if에 맞는 v-else랑 v-else-if  -->
  <!-- html 태그 속성에 데이터 바인딩할 때는 {{}}가 아니라 속성 앞에 : -->

  <div class = 'menu'>
    <a v-for = 'a in menus' :key = 'a'> {{a}} </a>
  </div>

  <DiscountBanner :discountRate = 'discountRate'/>

  <!-- <div v-for = '(a, i) in onerooms' :key = 'i'>
    <img :src="a.image" class = 'room_img'>
    <h4 @click = 'modalOpen = true'>{{a.title}} </h4>
    <p>{{a.price}}원</p>
  </div> -->

  <button @click="highToLow">높은 가격순 정렬</button>
  <button @click="lowToHigh">낮은 가격순 정렬</button>
  <button @click="sortByName">가나다순 정렬</button>
  <button @click="sortBack">정렬 초기화</button>

  <CardBanner @openModal = "modalOpen = true; modalPressed = $event"
   :oneroom = 'onerooms[i]' v-for='(a, i) in onerooms' :key= 'i'/>

</template>
   
<script>

import data from './assets/OneroomDetail.js';
import DiscountBanner from './DiscountBanner.vue'
import CardBanner from './CardBanner.vue'
import ModalComponent from './ModalComponent.vue'

export default {
  name: 'App',
  data(){
    return{
      oneroomsOriginal : [...data],
      modalPressed : 0,
      onerooms : data,
      reports : [0, 0, 0],
      menus : ['Home', 'Shop', 'About'],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      modalOpen : false,
      discountRate : 2,
    }
  },
  methods: {
    highToLow(){
      this.onerooms.sort(function(a, b){
        return b.price - a.price
      })
    },
    lowToHigh(){
      this.onerooms.sort(function(a, b){
        return a.price - b.price
      })
    },
    sortByName(){
      this.onerooms.sort(function(a, b){
        return a.title.localeCompare(b.title)
      })
    },
    sortBack(){
      this.onerooms = [...this.oneroomsOriginal]
    },
  },
  mounted(){
    setInterval(() => {
        this.discountRate --;
      }, 1000);
  },
  components: {
    DiscountBanner : DiscountBanner,
    CardBanner : CardBanner,
    ModalComponent : ModalComponent,
  }
}
</script>

<style>

.fade-enter-from{opacity: 0;}
.fade-enter-active{transition : 0.3s;}
.fade-enter-to{opacity: 1;}

.fade-leave-from{opacity: 1;}
.fade-leave-active{transition : 0.17s;}
.fade-leave-to{opacity: 0;}

body {
  margin : 0
}

div {
  box-sizing: border-box;
}

.black-bg {
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed; padding: 20px;
}

.white-bg{
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}

.room_img {
  width : 75%;
  margin-top: 30px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #24486c;
}

.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}

.menu {
  background: rgb(75, 66, 138);
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: rgb(237, 233, 233);
  padding: 10px;
}
</style>
