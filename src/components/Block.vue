<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        Click me!
    </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted() {
        console.log("component mounted.")
        setTimeout(() => {
            this.showBlock = true;
            this.startTimer()
        }, this.delay);
    },
    // updated() {
    //     console.log("component updated");
    // },
    // unmounted() {
    //     console.log("unmounted")
    // }
    methods: {
        startTimer() {
       this.timer = setInterval(() => {
    this.reactionTime +=10
       }, 10)
    },
    stopTimer() {
   clearInterval(this.timer)
   console.log(this.reactionTime)
   this.$emit('end', this.reactionTime)
    }
    }
}
</script>

<style>
.block {
    width: 400px;
    height: 200px;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    margin: 40px auto;
}
</style>