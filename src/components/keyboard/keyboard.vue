<template>
    <div class="containerKeyboard">
        <ul class="keyOperand">
            <li class="operand" @click="pushOperand($event)">+</li>
            <li class="operand" @click="pushOperand($event)">-</li>
            <li class="operand" @click="pushOperand($event)">/</li>
            <li class="operand" @click="pushOperand($event)">*</li>
            <li class="operand" @click="pushOperand($event)">c</li>
        </ul>
        <ul class="keyNumber">
            <li class="number" v-model="numbers" v-for="i in 10" @click="pushNumber(i)">
                {{i-1}}
            </li>
        </ul>
        <ul class="keyNumber">
            <li class="equal" @click="pushOperand($event)">=</li>
            <li class="point" @click="pushOperand($event)">⌫</li>
            <li class="point" @click="pushOperand($event)">.</li>
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
            if(el.target.innerHTML == 'c'){
                this.numbers = '';
                RelationComponents.$emit('getNumber',this.numbers)
            }else if(el.target.innerHTML == '='){
                this.numbers = eval(this.numbers);
                RelationComponents.$emit('getNumber',this.numbers)           
            }else if(el.target.innerHTML == '⌫'){
                this.numbers = this.numbers.slice(0, -1);
                RelationComponents.$emit('getNumber',this.numbers)                
            }else{
                this.numbers+=el.target.innerHTML
                RelationComponents.$emit('getNumber',this.numbers)
            }
        },
        pushNumber(val){
            this.numbers = (this.numbers.toString()).concat((val-1).toString());
            RelationComponents.$emit('getNumber',this.numbers)
            },
        },
        created() {
            document.addEventListener("keydown", funLog => {
                console.log(event)
                if(this.numbers != ''){
                    if(event.keyCode == 13){
                        this.numbers = eval(this.numbers);
                        RelationComponents.$emit('getNumber',this.numbers) 
                    }else if(event.keyCode == 8){
                        this.numbers = this.numbers.slice(0, -1);
                        RelationComponents.$emit('getNumber',this.numbers)   
                    }else if((event.keyCode >= 48 && event.keyCode <= 57) || (event.keyCode >= 96 && event.keyCode <= 105) || (event.keyCode == 187 || event.keyCode == 107 || event.keyCode == 189)){
                        if(event.key != '='){
                            this.numbers+=event.key
                            RelationComponents.$emit('getNumber',this.numbers)
                        }
                    }
                }else{
                    if((event.keyCode >= 48 && event.keyCode <= 57) || (event.keyCode >= 96 && event.keyCode <= 105)){
                        this.numbers+=event.key
                        RelationComponents.$emit('getNumber',this.numbers)
                    }
                }
            });  
        },
    }


</script>

<style scoped>
.keyOperand,.keyNumber{
    user-select: none;
    display: flex;
    list-style-type: none;
    flex-wrap: wrap;
    padding: 0;
}
.containerKeyboard{
    width: 100%;
}
.point,.equal,.operand,.number{
    user-select: none;
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
    width: 277px;
}
</style>