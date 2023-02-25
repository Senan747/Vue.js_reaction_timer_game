<template>
  <div class="block" v-if="showBlock" @click="stopTime">
    CLICK ME
  </div>
</template>

<script>
export default {
  props: ['delay'],
  data(){
    return{
      showBlock: false,
      timer: null,
      reactionTime: 0
    }
  },
  mounted(){
    setTimeout( () => {
      this.showBlock = true,
      this.startTime()
    }, this.delay)
  },
  methods: {
    startTime(){
        this.timer = setInterval(() => {
        this.reactionTime += 5
      }, 5)
    },
    stopTime(){
      clearInterval(this.timer),
      this.$emit('end', this.reactionTime)
    }
  }
}

</script>

<style>
  .block{
    width: 400px;
    background-color: #2c3e50;
    display:flex;
    justify-content: center;
    align-items:center;
    border-radius: 25px;
    color:white;
    font-size:20px;
    text-align: center;
    padding:100px;
    margin:40px auto;
    cursor:pointer;
    user-select: none;
  }
</style>