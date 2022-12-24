<script setup lang="ts">
    import {ref, computed, onMounted } from "vue"
    import { defineProps } from "vue";

    import puzzle_piece from './puzzle_piece.vue'
    import board_slot from './board_slot.vue'
    
    
    let board_stats = {
        'collumns': 5,
        'rows': 6
    }

    const spawnBoard = ({ collumns, rows }:any) => {
        let board = new Array(rows)

        // generates an array with rows and collumns and each item in the array is valued with an index related to the total tiles inside the upper array
        // tldr: array with 5 row 5 col, [4][4]=25 && [0][0]=0 if row and col count is 5, 
        let total_i = 0
        for (let col_i = 0; col_i < board.length; col_i++) { 
            board[col_i] = Array(collumns)
            for (let row_i = 0; row_i < board[col_i].length; row_i++) {
                total_i++
                board[col_i][row_i] = total_i
            }
        }

        return board
    }
    

    onMounted(() => {
        const solved = spawnBoard(board_stats)

        let puzz_board_container :any = document.querySelector('#puzz_board_container')
                
        board = document.querySelector('#board')
        board = board.getBoundingClientRect()
        board = {
            'width': board.width,
            'height': board.height,
            'xPos': board.x,
            'yPos': board.y,
            'aspectRatio': board.width / board.height,
            'colCount': solved[0].length,
            'rowCount': solved.length,
            'rect': board,
            'element': board = document.querySelector('#board')
        } 

        // console.log(board);
        
        // sets the rows and collumns of the board grid container
        board.element.style.setProperty('--rows', board.rowCount);
        board.element.style.setProperty('--cols', board.colCount);


        puzzle_pieces = document.querySelectorAll('.puzzle_piece')
        puzzle_pieces = {
            'elements': puzzle_pieces,
            'width': board.width / board.colCount,
            'height': board.height / board.rowCount,
            'count': board.colCount * board.rowCount
            // 'aspectRatio': 'needs to be spawned in first'
        }
        puzzle_pieces.aspectRatio = puzzle_pieces.width / puzzle_pieces.height

        // console.log(puzzle_pieces);
        
        // console.log({'puzz_board_container': puzz_board_container, 'board': board.element});
        // createBoard()
    });

    let board :any
    let puzzle_pieces :any

    const props = defineProps<{ 
        pieces: any;
        optional?: string;
    }>()

    console.log(props.pieces);
    
    
    
</script>

<template>
    <div id="puzz_board_container" class="puzz_board_container">
        <div id="board" class="board">
            <board_slot v-for="(slot, index) in parseInt(pieces)" :key="index" :board="board"></board_slot>
        </div>
        <puzzle_piece v-for="(piece, index) in parseInt(pieces)" :key="index"></puzzle_piece>
    </div>
</template>

<style>
    .puzz_board_container {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100vh;
    }

    #board {
        display: grid;
        grid-template-columns: repeat(var(--cols), 1fr);
        grid-template-rows: repeat(var(--rows), 1fr);
        background-color: var(--dark_1);
        aspect-ratio: 16 / 9;
        height: 60vh;
        
        position: absolute;
        translate: -50% -50%;
        --xPos: 50%;
        --yPos: 50%;
        left: var(--xPos);
        top: var(--yPos);
    }
</style>