<template>

  <div class = 'black-bg' v-if = 'modalOpen == true'>
    <div class = 'white-bg'>
      <h4>상세페이지</h4>
      <p>상세페이지 내용</p>
      <button @click = 'modalOpen = false'>닫기</button>
    </div>
  </div>

  <div class = 'menu'>
    <a v-for = 'a in menus' :key = 'a'> {{a}} </a>
  </div>

  <div>
    <img src="./assets/room0.jpg" class = 'room_img'>
    <h4 @click = 'modalOpen = true'>{{products[0]}} 원룸</h4>
      <p>50만원</p>
      <button @click = 'reports[0]++'>허위 매물 신고</button>
      <span>신고 수:{{reports[0]}} </span>
  </div>
  <div>
    <img src="./assets/room1.jpg" class = 'room_img'>
    <h4 @click = 'modalOpen = true'>{{products[1]}} 원룸</h4>
      <p>50만원</p>
      <button @click = 'reports[1]++'>허위 매물 신고</button>
      <span>신고 수:{{reports[1]}} </span>
  </div>
  <div>
    <img src="./assets/room2.jpg" class = 'room_img'>
    <h4 @click = 'modalOpen = true'>{{products[2]}} 원룸</h4>
      <p>50만원</p>
      <button @click = 'reports[2]++'>허위 매물 신고</button>
      <span>신고 수:{{reports[2]}} </span>
  </div>

</template>
   
<script>

export default {
  name: 'App',
  data(){
    return{
      reports : [0, 0, 0],
      menus : ['Home', 'Shop', 'About'],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      modalOpen : false
    }
  },
  methods: {
  },
  components: {
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
