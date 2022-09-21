<script>
    export default {
        name: "HealthBar",
        props: ["name", "position", "health"]
    }
</script>

<template>
    <div class="outerhealthdiv" v-bind:style="{top: position === 'top' ? '0px' : '', bottom: position === 'bottom' ? '0px' : ''}">
        <div class="healthdiv">
            <div class="innerhealthdiv" v-bind:style="{transform: `translateX(-${(100 - health)*0.8}vw)`, 'background-color': `rgb(${health >= 50 ? (50 - health/2)*6.8 : 170}, ${health >= 50 ? 170 : 170 - (50 - health)*3.4}, 0)`}" ></div>
        </div>
    </div>
</template>

<style scoped>
    .outerhealthdiv{
        position: absolute;
        left: 0px;
        width: 100vw;
        height: 10vh;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .healthdiv{
        width: 80%;
        height: 50%;
        background-color: rgba(0, 0, 0, 0.436);
        border-radius: 25%;
        overflow: hidden;
        opacity: 1;
    }
    .innerhealthdiv{
        width: 100%;
        height: 100%;
    }
</style>