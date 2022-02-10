<template>
  <p >Reaction Time: {{score}}ms</p>
  <p class="rank">{{rank}} </p>
</template>

<script>
export default {
    props: ['score'], 
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if (this.score < 250) {
            this.rank = 'Sharp!'
        } else if (this.score < 1000 ) {
            this.rank = "Fast!"
        } else if (this.score < 3000 ) {
            this.rank = "Good Going!"
        } else {
            this.rank = "Slug!"
        }
    },
}
</script>

<style>
    .rank {
        font-size: 1.4em;
        color: chocolate;
        font-weight: bold;
    }
</style>