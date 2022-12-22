<template lang="">
    <div>
        <p>Reaction time - {{ score }} ms</p>
        <p class="rank">Rank - {{ rank }}</p>
    </div>
</template>
<script>
export default {
    props: ['score'],
    data() {
        return {
            rank: null
        }
    },
    mounted () {
        if(this.score < 250) {
            this.rank = 'ninja fingers';
        } else if(this.score < 500) {
            this.rank = 'master reflexes';
        } else if(this.score < 1000) {
            this.rank = 'beginners pace';
        } else {
            this.rank = 'noob';
        }
    },
    methods: {
        // showResults() {
        //     this.showResults = true;
        // }
    }
}
</script>
<style>
    .rank{
        font-size: 1.4em;
        color: #0faf87;
        font-weight: bold;
    }
</style>