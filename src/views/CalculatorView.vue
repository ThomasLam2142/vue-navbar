<script setup>
import { ref } from 'vue'
let count = ref(0)
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


function equals(){
    if (currentOperator.value == '+'){
        console.log('performing addition')
        console.log(modValue.value)
        count.value = count.value + modValue.value
    }
    else if (currentOperator.value == '-'){
        console.log('performing subtraction')
        count.value = count.value - modValue.value
    }
    else{
        console.log('no operator selected')
    }

}

function clear(){
    currentOperator.value = ''
    count.value = 0
    modValue.value = 0
}

</script>

<template>
  <main>
    <h1>Calculator</h1>
    <div>
        {{ count }}
    </div>
    <div>
        {{ modValue }} {{ currentOperator }}
    </div>
    
    <div>
        <span>
            <button @click="add">+</button>
        </span>
        
        <span>
            <button @click="subtract">-</button>
        </span>
    </div>

    <div>
        <div>
            <span>
                <button @click="modValue = 1">1</button>
            </span>
            
            <span>
                <button @click="modValue = 2">2</button>
            </span>

            <span>
                <button @click="modValue = 3">3</button>
            </span>
        </div>

        <div>
            <span>
                <button @click="modValue = 4">4</button>
            </span>
            
            <span>
                <button @click="modValue = 5">5</button>
            </span>

            <span>
                <button @click="modValue = 6">6</button>
            </span>
        </div>

        <div>
            <span>
                <button @click="modValue = 7">7</button>
            </span>
            
            <span>
                <button @click="modValue = 8">8</button>
            </span>

            <span>
                <button @click="modValue = 9">9</button>
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

#equalsBtn{
    width: 100%;
    height: 100%;
}
</style>