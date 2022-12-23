<script setup lang="ts">

</script>

<template>
    <div class="nav_container">
        
        <div class="nav_item">
            <a href="" class="nav_link">
                <img src="../assets/svg/PuzzleFunLogo.svg" alt="Puzzle Fun Logo">
            </a>
        </div>

        <div class="nav_item">
            <a href="" class="nav_link">
                <img src="../assets/svg/Map.svg" alt="Map">
            </a>
        </div>

    </div>
</template>

<style>
    .nav_container {
        width: 100%;
        height: 12vh;
        background-color: var(--dark_1);
        box-shadow: 0px 0px 4px 4px rgba(0, 0, 0, 0.5);
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 1%;
    }

    .nav_item {
        height: 100%;
        aspect-ratio: 1;
        display: flex;
        justify-content: center;
        align-items: center;
        cursor: pointer;
    }

    .nav_link {
        display: block;
        height: 100%;
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
    }
</style>