<script setup lang="ts">
interface CounterProps {
    count: number,
    label: string,
    disabled?: boolean
}

defineProps<CounterProps>()

defineEmits<{
    increment: [number],
    decrement: [number],
    reset: []
}>()
</script>

<template>
    <section 
        class="flex items-center gap-2.5 transition-opacity "
        :class="{ 'pointer-events-none opacity-50 select-none line-through': disabled }"
    >
        <button 
            @click="$emit('increment', 1)"
            class="text-xl cursor-pointer opacity-50 bg-transparent border-0 text-white transition-opacity duration-300 hover:opacity-100 p-2"
        >
            +
        </button>
        <button 
            @click="$emit('decrement', 1)"
            class="text-xl cursor-pointer opacity-50 bg-transparent border-0 text-white transition-opacity duration-300 hover:opacity-100 p-2"
        >
            -
        </button>
        <h2 class="text-base m-0">
            {{ count }} {{ label }}{{ count !== 1 ? 's' : '' }}
        </h2>
        <button 
            @click="$emit('reset')"
            class="text-sm cursor-pointer opacity-50 bg-transparent border-0 text-white transition-opacity duration-300 hover:opacity-100 p-2"
        >
            Reset
        </button>
    </section>
</template>