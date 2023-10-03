<template>
    <p>time : {{ score }} ms</p>
    <p class="rank">Your rank : {{ rank }}</p>
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
            this.rank = 'Super fast'
        } else if (this.score < 400) {
            this.rank = 'Ok fast'
        } else {
            this.rank = 'Train more'
        }
    }
}
</script>

<style>
.rank{
    font-size: 1.5em;
    color: rgb(225, 38, 28);
    font-weight: bold;
}
</style>