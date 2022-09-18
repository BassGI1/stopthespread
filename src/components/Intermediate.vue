<script>
    export default {
        name: "Intermediate",
        methods: {
            pick: function(choice) {
                this.$emit('choice', choice)
                console.log(choice)
            }
        }
    }
</script>

<template>
    <div style="display: flex; justify-content: center; align-items: center; height: 100vh; width: 100vw;">
        <div class="option" style="background-color: rgb(127, 73, 146)" @click="pick('virus')">
            <img src="/Virus.png" alt="Virus" style="width: 100%; height: 100%; position: relative;">
            <img src="flame.gif" alt="flame" style="width: 30vw; position: relative; left: -10vw; top: -35vw;"/>
            <img src="flame.gif" alt="flame" style="width: 30vw; position: relative; right: -25vw; top: -69vw;"/>
            <img src="/virus_logo.png" alt="Virus Logo" style="position: relative; width: 70%; top: -243vh; left: 6vw;">
        </div>
        <div class="option" style="background-color: rgb(82, 166, 152);" @click="pick('antibody')">
            <img src="/Antibody.png" alt="Antibody" style="width: 100%; height: 90%; position: relative; top: 10%;">
            <img src="/greenting.gif" alt="Green Thing" style="width: 20vw; position: relative; top: -15vw;">
            <img src="/greenting.gif" alt="Green Thing" style="width: 20vw; position: relative; left: 6vw; top: -15vw;">
            <img src="/antibody_logo.png" alt="Antibody Logo" style="width: 70%; position: relative; top: -57vw; left: 7vw;">
        </div>
    </div>
</template>

<style scoped>
    .option{
        margin: 2vw;
        width: 45vw;
        height: 97vh;
        opacity: 0.5;
        border-radius: 2vh;
        cursor: pointer;
        overflow: hidden;
    }
    .option:hover{
        animation: opaq 0.5s forwards;
    }
    @keyframes opaq{
        100%{
            opacity: 1;
        }
    }
</style>