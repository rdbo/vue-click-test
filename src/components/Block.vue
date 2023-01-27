<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        <p>
            Click Me!<br/>
            (Delay: {{ delay }} ms)
        </p>
    </div>
</template>

<script>
export default {
    props : ["delay"],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime : 0
        };
    },

    mounted() {
        setTimeout(() => { this.showBlock = true; this.startTimer(); }, this.delay)
    },

    methods: {
        startTimer() {
            this.timer = setInterval(() => { this.reactionTime += 10; }, 10);
        },

        stopTimer() {
            clearInterval(this.timer);
            this.$emit("stop", this.reactionTime);
        }
    }
};
</script>

<style>
    .block {
        width: 400px;
        height: 400px;
        border-radius: 10px;
        background: green;
        color: white;
        display: flex;
        align-items: center;
        justify-content: center;
        margin: 32px auto;
    }
</style>
