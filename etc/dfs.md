## maze dfs

```js
let notFound = true;
let answer;

const go = (pos, maze, count, direction, dest) => {
  console.log("innerNotFound", notFound);
  const [y, x] = pos;
  if (y === dest[0] && x === dest[1]) {
    notFound = false;
    answer = count;
    return;
  }
  if (direction === "down") {
    if (notFound && x + 1 <= maze.length - 1 && maze[y][x + 1] !== 1) {
      go([y, x + 1], maze, count + 1, "right", dest);
    }
    if (notFound && y + 1 <= maze.length - 1 && maze[y + 1][x] !== 1) {
      go([y + 1, x], maze, count + 1, "down", dest);
    }
    if (notFound && x - 1 >= 0 && maze[y][x - 1] !== 1) {
      go([y, x - 1], maze, count + 1, "left", dest);
    }
    if (notFound && y - 1 >= 0 && maze[y - 1][x] !== 1) {
      go([y - 1, x], maze, count + 1, "top", dest);
    }
  } else if (direction === "right") {
    if (notFound && y - 1 >= 0 && maze[y - 1][x] !== 1) {
      go([y - 1, x], maze, count + 1, "top", dest);
    }
    if (notFound && x + 1 <= maze.length - 1 && maze[y][x + 1] !== 1) {
      go([y, x + 1], maze, count + 1, "right", dest);
    }
    if (notFound && y + 1 <= maze.length - 1 && maze[y + 1][x] !== 1) {
      go([y + 1, x], maze, count + 1, "down", dest);
    }
    if (notFound && x - 1 >= 0 && maze[y][x - 1] !== 1) {
      go([y, x - 1], maze, count + 1, "left", dest);
    }
  } else if (direction === "top") {
    if (notFound && x - 1 >= 0 && maze[y][x - 1] !== 1) {
      go([y, x - 1], maze, count + 1, "left", dest);
    }
    if (notFound && y - 1 >= 0 && maze[y - 1][x] !== 1) {
      go([y - 1, x], maze, count + 1, "top", dest);
    }
    if (notFound && x + 1 <= maze.length - 1 && maze[y][x + 1] !== 1) {
      go([y, x + 1], maze, count + 1, "right", dest);
    }
    if (notFound && y + 1 <= maze.length - 1 && maze[y + 1][x] !== 1) {
      go([y + 1, x], maze, count + 1, "down", dest);
    }
  } else {
    if (notFound && y + 1 <= maze.length - 1 && maze[y + 1][x] !== 1) {
      go([y + 1, x], maze, count + 1, "down", dest);
    }
    if (notFound && x - 1 >= 0 && maze[y][x - 1] !== 1) {
      go([y, x - 1], maze, count + 1, "left", dest);
    }
    if (notFound && y - 1 >= 0 && maze[y - 1][x] !== 1) {
      go([y - 1, x], maze, count + 1, "top", dest);
    }
    if (notFound && x + 1 <= maze.length - 1 && maze[y][x + 1] !== 1) {
      go([y, x + 1], maze, count + 1, "right", dest);
    }
  }
};

const solution = (maze) => {
  const start = [0, 0];
  const last = [maze.length - 1, maze.length - 1];
  go(start, maze, 0, "down", last);
  return answer;
};

console.log(
  solution([
    [0, 1, 0, 1],
    [0, 1, 0, 0],
    [0, 0, 0, 0],
    [1, 0, 1, 0],
  ])
);
```
