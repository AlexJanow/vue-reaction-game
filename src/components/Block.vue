<template>
    <div class="cheatProtection" v-if="cheatProtection" @click="abort"></div>
  <div class="block" v-if="showBlock" @click="stopTimer">
      click me
  </div>
</template>

<script>
export default {
    props: ["delay"],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0,
            cheatProtection: false
        }
    },
    beforeMount(){
            this.cheatProtection = true
    }
    ,
    mounted(){
        setTimeout(() => {
            this.cheatProtection = false
            this.showBlock = true
            this.startTimer()
        }, this.delay);
    },
    methods: {
        startTimer(){
            this.timer = setInterval(() => {
                this.reactionTime += 10
            },10)
        },
        stopTimer(){
            clearInterval(this.timer)
            this.$emit("end", this.reactionTime)
        },
        abort(){
            clearInterval(this.timer)
            this.$emit("abort", "too early :(")
        }
    }
}
</script>

<style>
    .cheatProtection{
        width: 400px;
        border-radius: 20px;
        background: transparent;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }

    .block {
        width: 400px;
        border-radius: 20px;
        background: #0faf87;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }

    @media only screen and (max-width: 600px) {
    .cheatProtection{
        width: 300px;
        border-radius: 20px;
        background: transparent;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }

    .block {
        width: 300px;
        border-radius: 20px;
        background: #0faf87;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }

}
</style>