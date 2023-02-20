<template>
    <div class="home">
    
        <h2>{{ appTitle }}</h2>
    
    
    
        <h3>{{ counterData.title }}:</h3>
    
    
    
        <div>
    
            
            <button @click="decreaseCounter(counterData.amount, $event)" class="btn">-</button>
            <span class="counter">{{ counterData.count }}</span>
            <button @click="increaseCounter(counterData.amount)" class="btn">+</button>
    
        </div>
        <p>This counter is {{ oddOrEven }}</p>
    
    
        <div class="edit">
    
            <h4>Edit counter title:</h4>
    
            <input v-model="counterData.title" type="text">
            <input v-model="counterData.amount" type="number">
    

        </div>
        
    </div>
</template>

<script setup >
import { reactive, computed, watch } from 'vue'
const appTitle = 'My Ok Counter App'
// const counter = ref(0),
//       counterTitle = ref('My Counter')
const oddOrEven = computed(() => {
   if(counterData.count %2 === 0){
    return 'even'
   } else {
    return 'odd'
   }
})
const counterData = reactive({
  count: 0,
  title: 'My Counter',
  amount: 3
})
watch(()=> counterData.count, (newCount, oldCount)=>{
    if(newCount=== 20){
        alert('Way to go! You made it to 20!!')
    }
})
const increaseCounter = (amount) => {

  counterData.count+=amount
}
const decreaseCounter = (amount, e) => {
  console.log(e)
    counterData.count-=amount
}
</script>

<style>
.home {
  text-align: center;
  padding: 20px;
}
.btn, .counter {
  font-size: 40px;
  margin: 10px;
}
.edit {
  margin-top: 60px;
}
</style>