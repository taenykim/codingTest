## maze bfs

```js
const board = [
  [0, 1, 0, 1],
  [0, 1, 0, 0],
  [0, 0, 0, 0],
  [1, 0, 1, 0],
];

const start = [0, 0];
const last = [board.length - 1, board.length - 1];
let count = 0;

const queue = [];

console.log("==============start===========");

const go = (start) => {
  const nextPositions = look(start);
  queue.push(...nextPositions);
  console.log("First next positions !! ", nextPositions);
  while (queue.length > 0) {
    if (start === last) {
      return board;
    }
    const target = queue.shift();
    console.log("target!!--!!", target);
    const nextPositions = look(target);
    console.log("next positions !! ", nextPositions);
    queue.push(...nextPositions);
    console.log("queue", queue);
    board[target[0]][target[1]] = -1;
    count++;
    console.log(board);
  }
};

const look = (pos) => {
  const answer = [];
  const [y, x] = pos;
  if (y + 1 <= board.length - 1 && board[y + 1][x] !== 1 && board[y + 1][x] === 0) {
    answer.push([y + 1, x]);
  }
  if (x + 1 <= board.length - 1 && board[y][x + 1] !== 1 && board[y][x + 1] === 0) {
    answer.push([y, x + 1]);
  }
  if (y - 1 >= 0 && board[y - 1][x] !== 1 && board[y - 1][x] === 0) {
    answer.push([y - 1, x]);
  }
  if (x - 1 >= 0 && board[y][x - 1] !== 1 && board[y][x - 1] === 0) {
    answer.push([y, x - 1]);
  }
  return answer;
};

go(start);
console.log(count);
```
