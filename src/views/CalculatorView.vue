<script setup>
import { ref } from 'vue'
let count = ref(0)
let modArray = ref([])
let modArray2 = ref([])    
let modValue = ref(0)
let modValue2 = ref(0)
let modStep = ref(0)

let currentOperator = ref('')

function add(){
    parseArrays()
    console.log('add')
    currentOperator.value = '+'
}


function subtract(){
    parseArrays()
    console.log('subtract')
    currentOperator.value = '-'
}

function multiply(){
    parseArrays()
    console.log('multiply')
    currentOperator.value = '*'
}

function divide(){
    parseArrays()
    console.log('divide')
    currentOperator.value = '%'
}

function equals(){
    console.log(modValue.value)
    if (modValue.value && modValue2.value){
        if (currentOperator.value == '+'){
            console.log('performing addition')
            count.value = modValue2.value + modValue.value
        }
        else if (currentOperator.value == '-'){
            console.log('performing subtraction')
            count.value = count.value - modValue.value
        }
        else if (currentOperator.value == '*'){
            console.log('performing multiplication')
            count.value = count.value * modValue.value
        }
        else if (currentOperator.value == '%'){
            console.log('performing division')
            count.value =  Math.floor(count.value/modValue.value) 
        }
        else{
            console.log('no operator selected')
        }
    }else{
        alert('Values not selected')
    }    

}

function parseArrays(){
    if (modStep.value == 0){
        modValue.value = parseInt(modArray.value.join(''))
        modStep.value = 1
    }
    else{
        modValue2.value = parseInt(modArray2.value.join(''))
        modStep.value = 0
    }
    
}

function clear(){
    currentOperator.value = ''
    count.value = 0
    modValue.value = 0
    modValue2.value = 0
    modArray.value = []
    modArray2.value = []
}


</script>

<template>
    <div class="card">
            <h1>Calculator</h1>
        <div id="mainDisplay">
            {{ count }}
        </div>
        <div>
            {{ modStep }}
        </div>
        <div>
            {{ modArray }} {{ currentOperator }} {{ modArray2 }}
        </div>
        
        <div>
            <span>
                <button @click="add">+</button>
            </span>
            
            <span>
                <button @click="subtract">-</button>
            </span>

            <span>
                <button @click="multiply">*</button>
            </span>
            
            <span>
                <button @click="divide">%</button>
            </span>
            <span>
                <button @click="modStep ===0 ? modArray.pop(): modArray2.pop()">Back</button>
            </span>
        </div>

        <div>
            <div>
                <span>
                    <button @click="modStep === 0 ? modArray.push('1') : modArray2.push('1')">1</button>
                </span>
                
                <span>
                    <button @click="modStep === 0 ? modArray.push('2') : modArray2.push('2')">2</button>
                </span>

                <span>
                    <button @click="modStep === 0 ? modArray.push('3') : modArray2.push('3')">3</button>
                </span>
            </div>

            <div>
                <span>
                    <button @click="modStep === 0 ? modArray.push('4') : modArray2.push('4')">4</button>
                </span>
                
                <span>
                    <button @click="modStep === 0 ? modArray.push('5') : modArray2.push('5')">5</button>
                </span>

                <span>
                    <button @click="modStep === 0 ? modArray.push('6') : modArray2.push('6')">6</button>
                </span>
            </div>

            <div>
                <span>
                    <button @click="modStep === 0 ? modArray.push('7') : modArray2.push('7')">7</button>
                </span>
                
                <span>
                    <button @click="modStep === 0 ? modArray.push('8') : modArray2.push('8')">8</button>
                </span>

                <span>
                    <button @click="modStep === 0 ? modArray.push('9') : modArray2.push('9')">9</button>
                </span>
            </div>
        </div>
        
        <div>
            <span>
                <button @click="equals" id="equalsBtn">=</button>
            </span>
            <span>
                <button @click="clear" id="clearBtn">clear</button>
            </span>
        </div>

    </div>


    
</template>

<style>

.card{
    width: 400px;
    height: 600px;
    border: 1px solid black;
    margin: auto;
    text-align: center;
    padding: 10px;

}

button{
    width: 30%;
    height: 40%;
}

#equalsBtn{
    width: 100%;
    height: 100%;
}

#mainDisplay{
    width: 100%;
    height: 100px;
    border: 1px solid black;
    text-align: right;
    padding-right: 10px;
    font-size: 50px;
    margin-bottom: 10px;
}
</style>