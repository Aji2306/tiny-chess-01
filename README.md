# tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in 4 KB of Python for make.fun's "Build the strongest chess engine in 4 KB of Python" bounty.

## What it does

`main.py` (3,111 bytes) is the whole engine: a 0x88-board negamax search with alpha-beta pruning, quiescence search, a transposition table, MVV-LVA + killer move ordering, and a material + piece-square-table evaluation. It searches to a fixed budget of 50,000 nodes per move (never a clock), so every trial replays deterministically. It plays the 16-game gauntlet through the env at `MAKEFUN_ENV_URL`.

The engine source is packed as an LZMA payload with a small unpacker (as the house sunfish baseline does), keeping the committed file under the 4,096-byte cap.

## Run

```sh
MAKEFUN_ENV_URL=http://store:8080 python3 -P -s main.py
```

It reads the game from the env, plays its moves in UCI, and exits when every game is over.
