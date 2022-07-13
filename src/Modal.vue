<template>
  <div>
      <div class="black_bg" v-if="modal_status == true">
        <div class="white_bg">
            <img :src="product[click_product].image">
            <h4>{{product[click_product].title}}</h4>
            <p>{{product[click_product].content}}</p>
            <input v-model = "month">

            <select v-model="month">
                <option>1</option>
                <option>2</option>
                <option>3</option>
                <option>4</option>
            </select>
            
            <p> {{month}}개월 선택{{product[click_product].price * month}}원</p>

            <button @click="$emit('close_modal',false)">닫기</button>
        </div>
      </div>
  </div>
</template>

<script>
export default {
    name: 'Model_te',
    data(){
        return {
            month:1,
        }
    },
    watch:{ // 데이터 감시 ( 데이터가 변할 때 마다 실행 )
        month(a){   // (month 변경 후 데이터, month 변경 전 데이터)
            if(a>=13){
                alert("13이상 입력 불가");
            }
            if(isNaN(a) == true){
                alert("문자 입력 불가");
                this.month = 1;
            }
        }
    },
    updated() {
        if(this.month == 2){
            alert("2 입력 불가")
        }
    },
    props :{    // props 받아온 데이터는 read only, 수정x
        modal_status: Boolean,
        product: Object,
        click_product: Number,
    }
}
</script>

<style>

</style>