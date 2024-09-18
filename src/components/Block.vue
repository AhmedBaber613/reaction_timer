<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    click me
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
        this.$emit('end', this.reactionTime)
        console.log(this.reactionTime)
      }
    }
  }
</script>

<style>
  .block {
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
  }
</style>

//20604090A
//https://us05web.zoom.us/j/4544299851?pwd=fOA6rZ2ab688TyqHn9uzt3c7rLXfV0.1&omn=89701135834