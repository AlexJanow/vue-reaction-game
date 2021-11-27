<template>
  <p class="time">Reaction time: {{score}} ms </p>
  <p class="rank"> {{rank}} </p>

</template>

<script>
export default {
    props: ["score"],
    data(){
        return {
            rank: null
        }
    },
    mounted(){
        if (this.score < 200){
            this.rank = "Eagle 🦅"
        }else if (this.score < 250){
            this.rank = "Leopard 🐆"
        }else if (this.score < 280){
            this.rank = "Cat 🐈"
        }else if (this.score < 300){
            this.rank = "Elephant 🐘"
        }else if (this.score < 350){
            this.rank = "Seal 🦭"
        }else if (this.score < 400){
            this.rank = "Sloth 🦥"
        }else if (this.score < 450){
            this.rank = "Turtle 🐢"
        }else {
            this.rank = "Snail 🐌"
        }
    }

}
</script>

<style>
    .time {
        font-size: 1em;
        color: white;
        font-weight: bold;
    }
    .rank {
        font-size: 2em;
        color: white;
        font-weight: bold;
    }
</style>