<script setup lang="ts">
import { computed } from 'vue'

interface CounterSummaryProps {
    counterLabel1: string,
    counterLabel2: string,
    itemLabel: string,
    data: any[]
}

const props = defineProps<CounterSummaryProps>()

defineEmits<{
    resetAll: []
}>()

const totalCount = computed(() =>
    props.data.reduce((sum, kind) => {
        return kind.disabled ? sum : sum + Number(kind.count)
    }, 0)
)

const totalFruitKinds = computed(() =>
    props.data.filter(kind =>
        !kind.disabled && Number(kind.count) > 0 && (kind.type=='fruit') 
    ).length
)
const totalVegetableKinds = computed(() =>
    props.data.filter(kind =>
        !kind.disabled && Number(kind.count) > 0 && (kind.type=='vegetable') 
    ).length
)
</script>

<template>
    <section class="text-xl mt-2.5">
        <p class="mb-2">Total {{ counterLabel1 }}: {{ totalFruitKinds }}</p>
        <p class="mb-2">Total {{ counterLabel2 }}: {{ totalVegetableKinds }}</p>
        <p class="mb-2">Total {{ itemLabel }}: {{ totalCount }}</p>
        <button 
            @click="$emit('resetAll')"
            class="text-sm cursor-pointer opacity-50 bg-transparent border-0 text-white transition-opacity duration-300 hover:opacity-100 p-2"
        >
            Reset all
        </button>
    </section>
</template>