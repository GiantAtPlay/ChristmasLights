<script setup>
    defineEmits(['mode-switch'])
</script>

<template>
    <div>
        <button @click="$emit('mode-switch', 'on')">On</button>
        <button @click="$emit('mode-switch', 'off')">Off</button>
        <button @click="$emit('mode-switch', 'flash')">Flash</button>
        <button @click="$emit('mode-switch', 'colours')">Colours</button>
        <button @click="$emit('mode-switch', 'chain')">Chain</button>
    </div>
</template>



<style scoped>

</style>