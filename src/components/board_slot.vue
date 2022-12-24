<script setup lang="ts">
    import { ref } from 'vue';

    
    defineProps<{ board: any }>()

    // console.log(board);
</script>

<template>
    <div class="puzz_slot">
        {{ board }}
    </div>
</template>

<style>
    .puzz_slot {
        outline: 3px solid var(--regular);
    }
</style>