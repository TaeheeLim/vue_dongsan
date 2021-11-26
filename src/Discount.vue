<template>
    <div class="discount">
        <h4>지금 결제하면 {{ 10- discountNumber }}% 할인</h4>
    </div>
</template>

<script>
export default {
    name: 'Discount',
    data(){
        return {
            discountNumber :0,
        }
    },
    mounted(){
        setInterval(() => {
            this.discountNumber += 1;
            if(this.discountNumber == 10){
                this.discountNumber = 0;
            }
        }, 1000);
    }
}
</script>

<style>

</style>