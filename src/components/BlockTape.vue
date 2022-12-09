<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        Tapeoooo ....
    </div>
</template>

<script>

export default {
    props: ['delay'],
    data(){
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    }, 
    // Lifecycle hooks
    mounted() {
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay);
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        stopTimer() {
            clearInterval(this.timer)
            console.log(this.reactionTime)
        }
    }
}
</script>

<style>
.block {
    background-color: #1565b6;
    border-radius : 50%;
    color: white;
    font-size: 2em;
    margin: 40px auto;
    padding: 100px 0;
    text-align: center;
    width: 250px;
}
</style>