<script setup lang="ts">
    import { ref, defineProps } from 'vue'

    const props = defineProps<{
        aspectRatio?: any;
    }>()

    console.log(props.aspectRatio);
    
</script>

<template>
    <div class="puzzle_piece">
        
    </div>
</template>

<style>
    .puzzle_piece {
        --piece-aspect-ratio: ;
        aspect-ratio: var(--piece-aspect-ratio);
    }
</style>