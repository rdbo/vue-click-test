<template>
    <h1>Reaction Timer</h1>
    <button @click="start" :disabled="isPlaying">Play Reaction Timer</button>
    <Block v-if="isPlaying" :delay="delay" @stop="stop"/>
    <p v-if="reactionTime != null">Reaction Time: {{ reactionTime }} ms</p>
</template>

<script>
import Block from "./components/Block.vue";

export default {
    name: 'App',
    components: { Block },
    data() {
        return {
            isPlaying : false,
            delay : null,
            reactionTime : null
        };
    },

    methods: {
        start() {
            this.delay = Math.round(2000 + Math.random() * 5000);
            this.reactionTime = null;
            this.isPlaying = true;
        },

        stop(reactionTime) {
            this.isPlaying = false;
            this.reactionTime = reactionTime;
        }
    }
}
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
