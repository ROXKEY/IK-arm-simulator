# Tower of Hanoi

A playable Tower of Hanoi with 3–8 disks, a move counter compared against the
theoretical minimum (2ⁿ − 1), and an auto-solve mode that animates the optimal
recursive solution.

## Run it

No dependencies — just open `index.html` in a browser, or use VS Code's Live
Server extension for auto-reload while editing.

## How it works

- **Manual play**: click a peg to pick up its top disk, click another peg to
  drop it — illegal moves (bigger disk onto smaller) are rejected with a message.
- **Auto-solve**: implements the classic recursive solution —
  `solve(n, from, to, via)` moves `n-1` disks out of the way, moves the largest
  disk, then moves the `n-1` disks back on top — and animates each move with a
  short delay.
