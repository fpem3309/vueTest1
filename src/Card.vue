<template>
  <div>
      <div>
        <img :src="product.image" class="test_img">
        <h4 @click="send">{{product.title}}</h4>
        <p>{{product.price}}원</p>
    </div>
  </div>
</template>

<script>
export default {
    name:'Card_te',
    props:{
        product : Object
    },
    methods:{
        send(){
            this.$emit('openModal', this.product.id)
        },
    }
}
</script>

<style>

</style>