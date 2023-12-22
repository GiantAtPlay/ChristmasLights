<script setup>
const props = defineProps({ index: Number, color: String, on: Boolean })
</script>

<template>
    <li :class="['light', `light-${index}`, props.color, { 'on': props.on }]"></li>
</template>

<style>
:root{
    --light-col: blue;
    --light-width: 15px;
    --light-height: 20px;
}

.light{
    background: var(--light-col);
    opacity: 0.4;
    width: var(--light-width);
    height: var(--light-height);
    border-bottom-left-radius: calc(var(--light-width)/ 2);
    border-bottom-right-radius: calc(var(--light-width)/ 2);
    
}

.light.blue{
    --light-col: blue;
}

.light.orange{
    --light-col: orange;
}

.light.green{
    --light-col: green;
}

.light.yellow{
    --light-col: gold;
}

.light.red{
    --light-col: red;
}

.light.on{
    opacity: 0.8;
    box-shadow: 0 0 15px 5px var(--light-col);
}
</style>
