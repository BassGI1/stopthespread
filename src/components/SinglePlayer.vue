<script>
    import Intermediate from './Intermediate.vue';
    export default {
    name: "SinglePlayer",
    components: { Intermediate },
    data() {
        return {
            renderIntermediate: true,
            player: 'idk'
        }
    }
}
</script>

<template>
    <div>
        <Intermediate v-if="renderIntermediate" @choice="(x) => {renderIntermediate = false; player = x;}"/>
        {{ player }}
    </div>
</template>

<style scoped>

</style>