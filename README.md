# Shopping List Counter — Summary

Purpose
- Small Vue 3 + TypeScript app to count grocery items and show a summary.

Key features used / learned
- Vue 3 Single File Components with <script setup lang="ts">
- TypeScript typing for props, emits and local interfaces
- Reactivity: ref for state, computed for derived values
- Parent↔child communication via props and emits
- List rendering with v-for and :key
- Simple guards (no negative counts) and disabled-item UI
- .vue TypeScript shim (vue-shim.d.ts)

Important files
- src/main.ts — app bootstrap
- src/App.vue — root state (kinds), handlers (increment/decrement/reset) and list rendering
- src/components/Counter.vue — reusable counter (props + emits)
- src/components/CounterSummary.vue — computed totals (items, fruit kinds, vegetable kinds)
- src/vue-shim.d.ts — .vue import type support for TypeScript

Run
- npm install
- npm run dev

