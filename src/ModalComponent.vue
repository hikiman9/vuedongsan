<template>
  <div class = 'black-bg' v-if = 'modalOpen == true'>
    <div class = 'white-bg'>
      <h4>{{onerooms[modalPressed].title}}</h4>
      <img :src="onerooms[modalPressed].image" style = "width: 100%">
      <p>{{onerooms[modalPressed].content}}</p>
      <input v-model.number = "month">
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
    props : {
        onerooms : Array,
        modalPressed : Number,
        modalOpen : Boolean,
    }
}
</script>

<style>

</style>