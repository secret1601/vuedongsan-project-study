<template>
    <!-- 모달창 -->
    <div class="black-bg" v-if="modal_open == true">
        <div class="white-bg">
        <h4>{{room[number].title}}</h4>
        <img :src="room[number].image" alt="이미지태그">
        <p>Info : {{room[number].content}}</p>
        <input v-model="month">
        <p> {{month}}개월 선택함 : 가격 {{room[number].price * month}}원</p>
        <button @click="$emit('modalClose')" class="modal-close">X 닫기</button>
        </div>
    </div>

</template>

<script>
export default {
    beforeUpdate(){
        if(this.month == 2) {
            alert('2는 ㄴㄴ');
            this.month = 3;
        }
    },
    name : 'ModalRead',
    data(){
        return {
            month : 1,
        }
    },
    watch : {
        // month라는 데이터가 변할 때마다 watcher가 실행된다.
        month(a) {
            if(a >= 13) {``
                alert('13이상 입력하지 마세요.')
            }
        },
    },

    props: {
        room: Object,
        number: Number,
        modal_open: Boolean
    },
}
</script>

<style>
    .black-bg {
    position: fixed;
    display: block;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.5);
    /* padding: 25px; */
    }

    .white-bg {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    display: block;
    width: 50%;
    background: #fff;
    border-radius: 20px;
    }
    .white-bg img {
    width: 80%;
    /* height: 100%; */
    }
    .modal-close {
    position: relative;
    border: 0;
    border-radius: 10px;
    background-color: wheat;
    text-align: center;
    padding: 5px 10px;
    }

</style>