
<script setup lang="ts">

import { ref } from 'vue'
import Counter from './components/Counter.vue'
import CounterSummary from './components/CounterSummary.vue'



interface Kind {
  label: string
  count: number
  type: 'fruit' | 'vegetable'
  disabled?: boolean
}


const kinds = ref<Kind[]>([
  { label: 'Orange', count: 0, type: 'fruit' },
  { label: 'Cucumber', count: 0, type: 'vegetable' },
  { label: 'Pineapple', count: 0, type: 'fruit', disabled: true },
  { label: 'Apple', count: 0, type: 'fruit' },  
  { label: 'Potato', count: 0, type: 'vegetable', disabled: true },
  { label: 'Carrot', count: 0, type: 'vegetable'}
])


const handleIncrement = (kind: Kind, amount: number): void => {
  kind.count += amount
}


const handleDecrement = (kind: Kind, amount: number): void => {
  if (kind.count - amount >= 0) kind.count -= amount
}


const resetAllCounts = (): void => {
  kinds.value.forEach((kind: Kind) => {
    kind.count = 0
  })
}




</script>



<template>
  <div class="min-h-screen bg-emerald-950 text-gray-100 flex items-center justify-center p-8 ">
    <div class="max-w-xl w-sm space-y-2 text-left py-3 px-4 border-2 rounded-xl">
      <h1 class="text-3xl font-bold mb-6 text-white">Shopping List Counter</h1>
      
      <Counter 
        v-for="kind in kinds" 
        :key="kind.label"
        :label="kind.label" 
        :count="kind.count"
        :disabled="kind.disabled"
        @increment="(amount:number) => handleIncrement(kind, amount)"
        @decrement="(amount:number) => handleDecrement(kind, amount)"
        @reset="kind.count=0"
      />
      <CounterSummary
        counterLabel1="fruits"
        counterLabel2="vegetables"
        itemLabel="items"
        :data="kinds"
        @resetAll="resetAllCounts"
      />
    </div>
  </div>
</template>