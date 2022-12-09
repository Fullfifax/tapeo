<template>
    <p class="reaction">
        Reaction time: {{ score }} ms <br> <br>
        <span>{{ rank }}</span>
    </p>
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
            this.rank = 'Izany ny enjana ;)'
        } else if (this.score < 450) {
            this.rank = 'Efa tsara :)'
        } else {
            this.rank = 'Aiza kosa e :('
        }
    }
}
</script>

<style>
.reaction {
    background-color: #1565b6;
    border-radius: 12px;
    color: white;
    margin: 20px auto;
    padding: 12px 16px;
    text-align: center;
    width: 200px;
}

.reaction span {
    font-size: 1.4em;
}
</style>