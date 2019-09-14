<template>
    <ul class="history">
        <li v-for="item in count" v-text="logHistory">{{item}}</li>
    </ul>
</template>

<script>
import { RelationComponents } from '../../main.js';

export default {
    data() {
        return {
            logHistory:'',
            count:'0'
        }
    },
    mounted(){
        RelationComponents.$on('submitExp',(data)=>{
            this.logHistory = data;
            this.count++;
            console.log(this.count);
        })
    },
}
</script>

<style scoped>
    .history{
        color: white;
        font-size: 3rem;
        padding: 20px;
        background: #0109172b;
        border-radius: 5px;
        margin: 0;
    }
</style>