<script setup>
// import HelloWorld from './components/HelloWorld.vue'
import Lights from "./components/Lights.vue";
import Light from "./components/Light.vue";
import ControlBox from "./components/ControlBox.vue";
import Tree from "./components/Tree.vue";
import {ref} from 'vue'

const mode = ref('off')

const onModeSwitch = (newMode)=> {
  mode.value = newMode
}

</script>

<template>
  <div class="scene">
    <div class="snow">
      <div></div>
    </div>
    <div class="ground">
      <ControlBox v-on:mode-switch="onModeSwitch"></ControlBox>
    </div>
    <div class="road"></div>
    <Tree>
      <Lights :mode="mode" v-slot="{index, blue, orange, green, yellow, red}">
        <Light :index="0" color="blue" :on="blue || index === 0" />
        <Light :index="1"  color="orange" :on="orange || index === 1" />
        <Light :index="2" color="green" :on="green || index === 2" />
        <Light :index="3" color="yellow" :on="yellow || index === 3" />
        <Light :index="4" color="red" :on="red || index === 4" />
        <Light :index="5" color="blue" :on="blue || index === 5" />
        <Light :index="6"  color="orange" :on="orange || index === 6" />
        <Light :index="7" color="green" :on="green || index === 7" />
        <Light :index="8" color="yellow" :on="yellow || index === 8" />
        <Light :index="9" color="red" :on="red || index === 9" />
        <Light :index="10" color="red" :on="red || index === 10" />
        <Light :index="11" color="blue" :on="blue || index === 11" />
        <Light :index="12"  color="orange" :on="orange || index === 12" />
      </Lights>
    </Tree>
  </div>
</template>

<style>
  :root{
    --road-height: 15%;
    --grass-height: 30%;
  }
  
  .scene{
    width: 100%;
    aspect-ratio: 16/9;
    border: 5px inset lightgoldenrodyellow;
    box-sizing: border-box;
    position: relative;
  }
  
  .road{
    position: absolute;
    bottom: 0;
    width: 100%;
    background: dimgrey;
    height: var(--road-height);
  }
  
  .ground{
    position: absolute;
    bottom: var(--road-height);
    width: 100%;
    background: whitesmoke;
    height: var(--grass-height);
  }
</style>
