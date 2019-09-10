<template>
    <div class="containerKeyboard">
        <ul class="keyOperand">
            <li class="operand" v-on:click="pushOperand($event.target.innerHTML)">+</li>
            <li class="operand" v-on:click="pushOperand($event.target.innerHTML)">-</li>
            <li class="operand" v-on:click="pushOperand($event.target.innerHTML)">/</li>
            <li class="operand" v-on:click="pushOperand($event.target.innerHTML)">*</li>
            <li class="operand" v-on:click="pushOperand($event.target.innerHTML)">c</li>
        </ul>
        <ul class="keyNumber">
            <li class="number" v-for="i in 10" v-model="numbers" @click="pushNumber(i)">
                {{i-1}}
            </li>
        </ul>
        <ul class="keyNumber">
            <li class="equal" v-on:click="pushOperand($event.target.innerHTML)">=</li>
            <li class="point" v-on:click="pushOperand($event.target.innerHTML)">.</li>
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
        pushOperand(el){
            if(el == 'c'){
                this.numbers = '';
                RelationComponents.$emit('getNumber',this.numbers)
            }else if(el == '='){
                this.numbers = eval(this.numbers);
                RelationComponents.$emit('getNumber',this.numbers)                
            }
            else{
                this.numbers+=el
                RelationComponents.$emit('getNumber',this.numbers)
            }
        },
        pushNumber(val){
            this.numbers = (this.numbers.toString()).concat((val-1).toString());
            RelationComponents.$emit('getNumber',this.numbers)
            },
        }
    }

</script>

<style scoped>
.keyOperand,.keyNumber{
    display: flex;
    list-style-type: none;
    flex-wrap: wrap;
    padding: 0;
}
.containerKeyboard{
    width: 100%;
}
.point,.equal,.operand,.number{
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
.equal{
    width: 382px;
}
</style>