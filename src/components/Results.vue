<template>
    <div>
        <h1>Results</h1>
        <p>Your average reaction time is: {{score}}ms</p>
        <p class="rank">Your have a {{ rank }} Reaction</p>
       
    </div>
</template>

<script>
export default {
    props: ['score'],
    data(){
        return {
            rank: null,
        }
    },
    mounted(){
        if(this.score < 300){
            this.rank = 'Rapid'
        }else if(this.score >= 300 && this.score < 500){
            this.rank = 'Normal'
        }else if(this.score >= 500){
            this.rank = 'Slow'
        }
    }
}
</script>

<style>
    .rank{
        font-size: 20px;
        color: #7fc88d;
        font-weight: bold;
    }
</style>