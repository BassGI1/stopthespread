<script>
    import Intermediate from './Intermediate.vue';
    import HealthBar from './HealthBar.vue';
    export default {
    name: "SinglePlayer",
    components: { Intermediate, HealthBar },
    data() {
        return {
            renderIntermediate: true,
            player: '',
            name: '',
            animateButton: false,
            renderGame: false,
            health: 100
        }
    },
    methods: {
        start: function() {
            this.animateButton = true
            //setTimeout(() => {this.renderGame = true}, 8000)
            this.renderGame = true
            //change this back after done making the game
        }
    }
}
</script>

<template>
    <div style="height: 100vh; width: 43vw; align-items: center; justify-content: center; display: flex; flex-wrap: wrap;">

        <Intermediate v-if="renderIntermediate" @choice="(x) => {renderIntermediate = false; player = x;}"/>
        <h1 v-if="player !== '' && !renderGame">You are playing as the {{ player }}. Name your {{ player }}:</h1>
        <input type="text" v-model="name" v-if="player !== '' && !renderGame" style="margin-top: -50vh;" :placeholder="player">
        <div class="startbutton" v-if="player !== '' && !renderGame" @click="start()" v-bind:class="{animateButton: animateButton}">{{ animateButton ? '' : ' Begin! ' }}</div>
    </div>

    <div class="gamediv" v-if="renderGame">
        <HealthBar :name="name" :position="'top'" :health="health" />
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
    .gamediv{
        position: absolute;
        left: 0px;
        top: 0px;
        width: 100vw;
        height: 100vh;
        background: url(/background_2.jpg) no-repeat center center fixed;
        background-size: 100%;
    }
</style>