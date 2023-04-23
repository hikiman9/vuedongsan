<template>
  <div class = 'black-bg' v-if = 'modalOpen == true'>
    <div class = 'white-bg'>
      <h4>{{onerooms[modalPressed].title}}</h4>
      <img :src="onerooms[modalPressed].image" style = "width: 100%">
      <p>{{onerooms[modalPressed].content}}</p>
      <input v-model = "month">
      <p>{{month}}개월 선택 시: {{onerooms[modalPressed].price * month}}원</p>
      <button @click = "$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
    name : 'ModalComponent',
    data(){
      return{
        month : 1,
      }
    },
    watch : {
      month(a){
        if(a >= 13){
          this.month = 1
          alert("12개월까지 구매 가능합니다.")
        } else if(isNaN(a)){
          this.month = 1
          alert("숫자를 입력해주십시오.")
        }
      }
    },
    // watch : {
    //   month(a){
    //     if(a >= 13){
    //       alert("12개월까지 구매 가능합니다.")
    //       this.month = 1
    //     } else if(a.isNaN()){
    //       alert("숫자를 입력해주십시오.")
    //       this.month = 1
    //     } 
    //   }
    // },
    props : {
        onerooms : Array,
        modalPressed : Number,
        modalOpen : Boolean,
    }
}
</script>

<style>

</style>