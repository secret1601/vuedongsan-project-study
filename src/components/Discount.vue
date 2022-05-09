<template>
    <div class="discount">
        <h4>
            지금 결제하면 
            <i class="dis-sale">{{sale}}% </i>
            할인
        </h4>
        <span class="dis-info">늦게 구매할수록 할인율이 더욱 낮아져요 ! !</span>
    </div>
</template>

<script>
export default {
    name: 'App',
    data(){
        return {
            sale: 40
        }
    },

    mounted(){
        let ace = setInterval(() => {
            this.sale--;
            if(this.sale == 0) {
                clearInterval(ace);
            }
        }, 1000);
    
    }

}
</script>

<style>
    .discount {
        background: #eee;
        padding: 10px;
        margin: 10px;
        border-radius: 5px;
    }
    .dis-sale {
        color: rgb(119, 0, 255);
        background-color: rgba(139, 103, 56, 0.349);
        border-radius: 4px;
        padding: 0 2px;
    }
    .dis-info {
        font-size: 14px;
        color: red;
        font-weight: bold;
    }

</style>