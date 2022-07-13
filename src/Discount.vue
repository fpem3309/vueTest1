<template>
  <div>
      <div class="discount">
         <h4> Component {{obj['name']}} 할인{{amount}}%</h4>
       </div>
  </div>
</template>

<script>
export default {
    name: 'Discount_te',
    props:{
        obj: Object,
        amount: Number
    }
    
}
</script>

<style>

</style>