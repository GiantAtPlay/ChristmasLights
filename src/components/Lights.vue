<script setup>
    import {computed, ref, watch} from 'vue'
    
    const allColors = ['blue', 'orange', 'green', 'yellow', 'red']
    
    const props = defineProps(['mode'])
    const colorsOn = ref([]);
    const indexOn = ref(null);
    
    const blueState = computed(()=> {
        return colorsOn.value.includes('blue')
    })
    const orangeState = computed(()=> {
        return colorsOn.value.includes('orange')
    })
    const greenState = computed(()=> {
        return colorsOn.value.includes('green')
    })
    const yellowState = computed(()=> {
        return colorsOn.value.includes('yellow')
    })
    const redState = computed(()=> {
        return colorsOn.value.includes('red')
    })
    
    let flashInterval;
    let coloursInterval;
    let chainInterval;
    
    watch(()=> props.mode, (n)=>{
        reset()
        if(n === 'on'){
            colorsOn.value = ['blue', 'orange', 'green', 'yellow', 'red']
        }
        
        if(n === 'off'){
            colorsOn.value = []
        }
        
        if(n === 'flash'){
            let flashOn = false;
            flashInterval = setInterval(()=> {
                if(flashOn){
                    colorsOn.value = []
                } else{
                    colorsOn.value = ['blue', 'orange', 'green', 'yellow', 'red']
                }
                flashOn = !flashOn
            }, 1000)
        }
        
        if(n === 'colours'){
            let index = 0
            coloursInterval = setInterval(()=> {
                const col = allColors.at(index)
                colorsOn.value = [col]
                
                if(index < 4) index++
                else index = 0
            }, 500)
        }
        
        if(n === 'chain'){
            let lights = document.querySelectorAll('.light')
            let index = 0
            chainInterval = setInterval(()=> {
                indexOn.value = index
                if(index < lights.length) index++
                else index = 0
            }, 300)
        }
    })
    
    const reset = ()=> {
        clearInterval(flashInterval)
        clearInterval(coloursInterval)
        clearInterval(chainInterval)
        indexOn.value = null
        colorsOn.value = []
    }
</script>

<template>
    <ul class="lights">
        <slot :index="indexOn" :blue="blueState" :orange="orangeState" :green="greenState" :yellow="yellowState" :red="redState"></slot>
    </ul>
</template>

<!--suppress CssUnusedSymbol -->
<style>
.lights{
    z-index: 10;
    position: absolute;
    width: 100%;
    height: 120%;
    bottom: 10%;
    margin: 0 0;
    padding: 0 0;
    list-style: none;
}

.light{
    position: absolute;
    transform: translateX(-50%);
}

.light-0{top: 5%;left: 45%;}
.light-1{top: 9%;left: 57%;}
.light-2{top: 20%;left: 35%;}
.light-3{top: 27%;left: 48%;}
.light-4{top: 34%;left: 60%;}
.light-5{top: 42%;left: 70%;}
.light-6{top: 50%;left: 30%;}
.light-7{top: 58%;left: 45%;}
.light-8{top: 68%;left: 60%;}
.light-9{top: 75%;left: 75%;}
.light-10{top: 80%;left: 25%;}
.light-11{top: 88%;left: 40%;}
.light-12{top: 95%;left: 55%;}
</style>