<template>
    <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
        <img :src="원룸들[누른거].image" style="width:40%">
        <h4>{{ 원룸들[누른거].title }}</h4>
        <h4>{{ 원룸들[누른거].content }}</h4>
        <!-- <input @input="months = $event.target.value"> -->
        <input v-model="months">
        <input type="range" min="1" max="12">
        <!-- <textarea v-model="months"></textarea> -->
        <!-- <input type="checkbox" v-model="months"> -->
<!-- 
        <select v-model="months">
            <option value="1">1</option>
            <option value="2">2</option>
            <option value="3">3</option>
        </select> -->
        <h4>{{ months }} 개월 선택 함: {{ 원룸들[누른거].price * months }}원</h4>
        <button @click="$emit('closeModal')">닫기</button>
    </div>
    </div>
</template>

<script>
export default {
    name : 'Modal',
    data() {
        return {
            months : 1,
        }
    },
    watch : {
        months(a){
            if (a > 13) {
                alert('13이상 입력 안된다');
                this.months = 1
            }
            if(isNaN(a) == true){
                alert('문자입력안됨');
                this.months = 1
            }
        },
    },
    props : {
        원룸들 : Array,
        누른거 : Number,
        모달창열렸니 : Boolean,
    },
    beforeUpdate() {
        if(this.months == 2){
            alert('2개월 노노')
            this.months = 1;
        }
    },
}
</script>

<style>

</style>