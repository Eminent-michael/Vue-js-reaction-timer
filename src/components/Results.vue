<template>
    <h2>{{ clickRate }}</h2>
</template>

<script>
    export default{
        props: ["result", "show"],

        data() {
            return{
                clickRate: null,
            }
        },
        mounted() {
            if (this.result < 250) {
                this.clickRate = "Flash Finger"
            }else if(this.result < 400) {
                this.clickRate = "Rapid Reflexes"
            }else{
            console.log(this.result)
                this.clickRate = "Snail Pace...."
            }
        },
    }
</script>

<style>
    h2 {
        color: #0faf87;
    }
</style>