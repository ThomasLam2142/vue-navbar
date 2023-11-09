<script setup>
import { ref } from 'vue'
let count = ref(0)
let modArray = ref([])
let modValue = ref(0)
let currentOperator = ref('')

function add(){
    console.log('add')
    currentOperator.value = '+'
}


function subtract(){
    console.log('subtract')
    currentOperator.value = '-'
}

function multiply(){
    console.log('multiply')
    currentOperator.value = '*'
    console.log(currentOperator.value)
}

function divide(){
    console.log('divide')
    currentOperator.value = '%'
    console.log(currentOperator.value)
}

function equals(){
    modValue.value = parseInt(modArray.value.join(''))
    console.log(modValue.value)
    if (currentOperator.value == '+'){
        console.log('performing addition')
        count.value = count.value + modValue.value
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

}

function clear(){
    currentOperator.value = ''
    count.value = 0
    modValue.value = 0
    modArray.value = []
}


</script>

<template>
  <main>
    <h1>Calculator</h1>
    <div id="mainDisplay">
        {{ count }}
    </div>
    <div>
        {{ modArray }} {{ currentOperator }}
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
            <button @click="modArray.pop()">Back</button>
        </span>
    </div>

    <div>
        <div>
            <span>
                <button @click="modArray.push('1')">1</button>
            </span>
            
            <span>
                <button @click="modArray.push('2')">2</button>
            </span>

            <span>
                <button @click="modArray.push('3')">3</button>
            </span>
        </div>

        <div>
            <span>
                <button @click="modArray.push('4')">4</button>
            </span>
            
            <span>
                <button @click="modArray.push('5')">5</button>
            </span>

            <span>
                <button @click="modArray.push('6')">6</button>
            </span>
        </div>

        <div>
            <span>
                <button @click="modArray.push('7')">7</button>
            </span>
            
            <span>
                <button @click="modArray.push('8')">8</button>
            </span>

            <span>
                <button @click="modArray.push('9')">9</button>
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
  </main>
</template>

<style>

button{
    width: 30%;
    height: 30%;

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