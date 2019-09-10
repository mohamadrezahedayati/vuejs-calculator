<template>
    <div id="app">
       <div class="cal">
            <monitor></monitor>
            <keyboard></keyboard>
       </div>
    </div>
</template>

<script>

import keyboard from './components/keyboard/keyboard.vue'
import monitor from './components/monitor/monitor.vue'

export default {
    name: 'App',
    data() {
        return {
            
        }
    },
    components:{keyboard,monitor}
}
</script>

<style>
.cal{
    background:linear-gradient(0deg, #540355 ,#4e014f );
    display: flex;
    justify-content: center;
    align-content: center;
    flex-direction: column;
    align-items: center;
    border: 5px #ad59ae solid;
    width: 530px;
    padding: 1rem;
    border-radius: 7px;
    margin: 0 auto;
}
</style>
