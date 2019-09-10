<template>
    <div class="containerKeyboard">
        <ul class="keyOprator">
            <li class="oprator" v-on:click="pushOprator($event)">+</li>
            <li class="oprator" v-on:click="pushOprator($event)">-</li>
            <li class="oprator" v-on:click="pushOprator($event)">%</li>
            <li class="oprator" v-on:click="pushOprator($event)">x</li>
            <li class="oprator" v-on:click="pushOprator($event)">c</li>
        </ul>
        <ul class="keyNumber">
            <li class="number" v-for="i in 10" v-model="numbers" @click="pushNumber(i)">
                {{i-1}}
            </li>
        </ul>
    </div>
</template>

<script>

import { RelationComponents } from '../../main.js';

export default {
    data() {
        return {
            numbers:''
        }
    },
    methods:{
        pushNumber(val){
            this.numbers = (this.numbers.toString(16)).concat((val-1).toString(16));
            console.log(this.numbers)
            RelationComponents.$emit('getNumber',this.numbers)
        },
        pushOprator(el){
            console.log(el.target);
            }
        }
    }

</script>

<style scoped>
.keyOprator,.keyNumber{
    display: flex;
    list-style-type: none;
    flex-wrap: wrap;
    padding: 0;
}
.containerKeyboard{
    width: 100%;
}
.oprator,.number{
    text-align: center;
    height: 65px;
    font-size: 45px;
    width: 65px;
    box-shadow: 1px 3px 5px #0000006b;
    color: white;
    border: 1px #ee9eef solid;
    background-color: #8f0a5a;
    padding: 12px;
    margin: 7px;
    border-radius: 2px;
    line-height: 65px;
    text-shadow: 0px 0px 4px #fcf7f7d6;
}
</style>