<template>
    <div>

        <img :src="room.image" alt="룸1" class="room-img">
        <h4 @click="send()">{{ room.title }}</h4>
        <p>{{room.price}}원</p>

    </div>
</template>

<script>
export default {
    name: 'RoomList',
    props: {
        room: Object,
        // number: Number,
        신고수: Array
    },
    methods : {
        send(){
            this.$emit('openModal', this.room.id)
        }
    }
}
</script>

<style>
    .room-img {
        width: 90%;
    }
</style>