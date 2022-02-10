<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
      Click Me
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
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        stopTimer() {
            clearInterval(this.timer)
            this.$emit('ended', this.reactionTime)
        }
    }
    // updated() {
    //     console.log('updated')
    // },
    // unmounted() {
    //     console.log('unmounted')
    // },
}
</script>

<style>
    .block {
        width: 300px;
        border-radius: 20px;
        background:  rgb(211, 152, 41);
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
        color: aliceblue;
    }
</style>