<script setup lang="ts">
    import {ref, onMounted} from "vue"
    
    

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
        console.log(board);
        
        return board
    }


    const createBoard = () => {
        const solved = new Array(spawnBoard(board_stats))
        console.log(solved);


        onMounted(() => {
            let puzz_board_container :any = document.querySelector('#puzz_board_container'),
                board :any = document.querySelector('#board') 

            // sets the rows and collumns of the board grid container
            board.style.setProperty('--rows', solved[0].length);
            board.style.setProperty('--cols', solved[0][0].length);
            
            let slot_i = 0
            for (let col_i = 0; col_i < solved[0].length; col_i++) { 
                for (let row_i = 0; row_i < solved[0][0].length; row_i++) {
                    slot_i++
                    
                    let board_slot = document.createElement('div')
                    board_slot.classList.add('puzz_slot')
                    board?.appendChild(board_slot)


                    let board_slot_piece : any = document.createElement('div')
                    board_slot_piece.innerHTML = slot_i
                    puzz_board_container?.appendChild(board_slot_piece)
                }
            }

            
            console.log({'puzz_board_container': puzz_board_container, 'board': board});
        });
    }
    
   
    
    createBoard()
</script>

<template>
    <div id="puzz_board_container" class="puzz_board_container">
        <div id="board" class="board"></div>
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

    .puzz_slot {
        outline: 3px solid var(--regular);
    }
</style>