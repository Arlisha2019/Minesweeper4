# Minesweeper4

class Board {
  constructor(numberOfRows, numberOfColumns, numberOfBombs) {
    this._numberOfBombs = numberOfBombs;
    this._numberOfTiles = (numberOfRows * numberOfColumns);
    this._playerBoard = Board.generatePlayerBoard(numberOfRows, numberOfColumns);
    this._bombBoard = Board.generateBombBoard(numberOfRows, numberOfColumns, numberOfBombs);
  }
get playerBoard() {
  return this._playerBoard;
   }

     flipTile(rowIndex, columnIndex) {
   if (this._playerBoard[rowIndex][columnIndex] !== ' ') {
    return;
   } else if (bombBoard[rowIndex][columnIndex] === 'B') {
    this._playerBoard[rowIndex][columnIndex] = 'B';
   } else {
     this._playerBoard[rowIndex][columnIndex] = this.getNumberOfNeighborBombs(rowIndex, columnIndex);
     this._numberOfTiles--;
   }
   getNumberOfNeighborBombs(rowIndex, columnIndex);
   neighborOffsets = [
    [0, 1],
    [1, 1],
    [-1, 1],
    [0, -1],
    [-1, -1],
    [1, -1],
    [0, 1],
    [1, 0]];
   const numberOfRows = this._bombBoard.length;
  const numberOfColumns = this._bombBoard[0].length;
   let numberOfBombs = 0;
    neighborOffsets.forEach(offset => {
  const  neighborRowIndex = rowIndex + offset[0];
  const neighborColumnIndex = columnIndex + offset[1];
     if (neighborRowIndex >= 0 && neighborRowIndex < numberOfRows && neighborColumnIndex >= 0 && neighborColumnIndex < numberOfColumns) {
       if(bombBoard[neighborRowIndex][neighborColumnIndex] =='B') {
         numberOfBombs++;
       }
     }
   });
   return numberOfBombs;
   }
   hasSafeTiles() {
    return this._numberOfTiles !== this._numberOfBombs;
     }
   }
   static generatePlayerBoard(numberOfRows, numberOfColumns) {
   let board = [];
   for (let rows = 0; rows < numberOfRows; rows++) {
     const rows = [];
       for (let columns = 0; columns < numberOfColumns; columns++) {
        rows.push(' ');
      }
      board.push(rows);
     }
     return board;
   };
   static generateBombBoard(numberOfRows, numberOfColumns, numberOfBombs) {
     let board = [];
     for (let rows = 0; rows < numberOfRows; rows++) {
       const rows = [];
         for (let columns = 0; columns < numberOfColumns; columns++) {
          rows.push(null);
        }
        board.push(rows);
       }
       let numberOfBombsPlaced = 0;
       while (numberOfBombsPlaced < numberOfBombs) {
         let randomRowIndex = Math.floor(Math.random() * numberOfRows);
         let randomColumnIndex = Math.floor(Math.random() * numberOfColumns);
         if (board[randomRowIndex][randomColumnIndex] !== 'B') {
           board[randomRowIndex][randomColumnIndex] = 'B';
           numberOfBombsPlaced++;
         }
         // This code in your while loop has the potential to place bombs on top of already existing bombs. This will be fixed when learn about control flow.
       }
       return board;
   };
}





}
print(board) {
console.log(board.map(row => row.join(' | ')).join('\n'));
  };


let this._playerBoard = generatePlayerBoard(3, 3);
let this._bombBoard = generateBombBoard(3, 3, 3);

console.log('Player Board: ');
printBoard(this._playerBoard);
console.log('Bomb Board: ');
printBoard(this._bombBoard);
flipTile(this._playerBoard, this._bombBoard, 0, 1);
console.log('Update Player Board:');
printBoard(this._playerBoard);
