<template>
  <div>
    <img :src="oneroom.image" class = 'room_img'>
    <!-- <h4 @click = 'modalOpen = true; modalPressed = i'>{{a.title}} </h4> -->
    <p>{{oneroom.price}}원</p>
  </div>
</template>

<script>
export default {
    name : 'CardBanner',
    props : {
        oneroom : Object,
    }

}
</script>

<style>

</style>