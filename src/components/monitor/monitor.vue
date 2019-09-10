<template>
    <div class="containerMonitor">
        <div>
            <h2 class="monitor" v-text="showMonitor"></h2>
            <h4 class="preview">
                <span>preview : </span>
                <span v-text="previewShowMonitor"></span>
            </h4>
        </div>
    </div>
</template>

<script>

import { RelationComponents } from '../../main.js';

export default {
    data() {
        return {
            showMonitor:'',
            previewShowMonitor:''
        }
    },
    mounted() { 
        RelationComponents.$on('getNumber',(data)=>{
            this.showMonitor = data;
            this.previewShowMonitor = eval(data);
        })
    },
    
}
</script>

<style scoped>
.monitor{   
    margin: 0;
    padding: 20px;
    font-size: 2.2rem;
    border: 4px #191919 solid;
    background-color: #cecece;
    box-shadow: inset 0px 0px 8px 2px #7a7575;
    border-radius: 7px;
    color: #1c1a1a;
    filter: drop-shadow(0px 6px 9px #1c1a1a);
}
.containerMonitor{
    width: 100%;
}
.preview{
    color: white;
    margin: 10px 25px;
}
</style>