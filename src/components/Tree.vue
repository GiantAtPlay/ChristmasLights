<script setup>

</script>

<template>
    <div class="tree-wrapper">
        <div class="star"></div>
        <div class="triangle"></div>
        <div class="triangle two"></div>
        <div class="triangle three"></div>
        <div class="triangle four"></div>
        <div class="triangle five"></div>
        <div class="trunk"></div>
        <slot></slot>
    </div>
</template>

<style scoped>
    .tree-wrapper{
        position: absolute;
        height: 50%;
        width: 30%;
        right: 10%;
        bottom: calc(var(--road-height) + 10%);
    }
    .triangle{
        position: absolute;
        width: 100%;
        height: 50%;
        bottom: 10%;
        left: 50%;
        transform: translateX(-50%);
        background: #034f33;
        clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
        z-index: 3;
    }
    
    .triangle.two{
        bottom: 30%;
        width:85%;
    }
    .triangle.three{
        bottom: 50%;
        width: 75%;
    }
    .triangle.four{
        bottom: 70%;
        width: 60%;
    }
    .triangle.five{
        bottom: 90%;
        width: 50%;
    }
    
    .trunk{
        position: absolute;
        background: #66503e;
        height:15%;
        width: 15%;
        bottom: -5%;
        left: 50%;
        transform: translateX(-50%);
    }
</style>