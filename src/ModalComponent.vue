<template>
  <div class = 'black-bg' v-if = 'modalOpen == true'>
    <div class = 'white-bg'>
      <h4>{{onerooms[modalPressed].title}}</h4>
      <img :src="onerooms[modalPressed].image" style = "width: 100%">
      <p>{{onerooms[modalPressed].content}}</p>
      <p>{{onerooms[modalPressed].price}}원</p>
      <button @click = 'modalOpen = false'>닫기</button>
    </div>
  </div>
</template>

<script>
export default {
    name : 'ModalComponent',
    props : {
        onerooms : Array,
        ModalPressed : Number,
        ModalOpen : Boolean,
    }
}
</script>

<style>

</style>