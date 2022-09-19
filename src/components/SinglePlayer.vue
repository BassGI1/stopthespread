<script>
    import Intermediate from './Intermediate.vue';
    export default {
    name: "SinglePlayer",
    components: { Intermediate },
    data() {
        return {
            renderIntermediate: true,
            player: '',
            name: '',
            animateButton: false
        }
    },
    methods: {
        start: function() {
            this.animateButton = true
        }
    }
}
</script>

<template>
    <div style="height: 100vh; width: 43vw; align-items: center; justify-content: center; display: flex; flex-wrap: wrap;">
        <Intermediate v-if="renderIntermediate" @choice="(x) => {renderIntermediate = false; player = x;}"/>
        <h1 v-if="player !== ''">You are playing as the {{ player }}. Name your {{ player }}:</h1>
        <input type="text" v-model="name" v-if="player !== ''" style="margin-top: -50vh;" :placeholder="player">
        <div class="startbutton" v-if="player !== ''" @click="start()" v-bind:class="{animateButton: animateButton}">{{ animateButton ? '' : ' Begin! ' }}</div>
    </div>
</template>

<style scoped>
    .startbutton{
        position: absolute;
        bottom: 20vh;
        cursor: pointer;
        font-size: 3rem;
        background-color: blueviolet;
        width: 12vw;
        height: 12vh;
        border-radius: 2vh;
        display: flex;
        justify-content: center;
        align-items: center;
        box-sizing: border-box;
        background-clip: content-box
    }
    .animateButton{
        animation: animateButton 0.5s both, animateButtonColour 3s infinite;
    }
    @keyframes animateButton{
        0%{
            width: 12vw;
            height: 12vh;
        }
        100%{
            width: 4vw;
            height: 4vw;
            border-radius: 50%;
            padding: 2vw;
            box-shadow: inset 0 0 0 2vw purple;
        }
    }
    @keyframes animateButtonColour {
        0%{
            padding: 2vw;
            box-shadow: inset 0 0 0 1vw purple;
            cursor: default;
        }
        50%{
            padding: 2vw;
            box-shadow: inset 0 0 0 1vw rgb(15, 15, 147);
            cursor: default;
        }
        100%{
            padding: 2vw;
            box-shadow: inset 0 0 0 1vw purple;
            cursor: default;
        }
    }
</style>