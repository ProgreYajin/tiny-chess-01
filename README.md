[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/ProgreYajin/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/ProgreYajin/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

# tiny-chess-01 entry

`main.py` is the whole engine: at most 4,096 bytes of Python 3.13, standard
library only, packed as a zlib/lzma payload with its unpacker.

- Board: 120-square mailbox, always seen from the side to move.
- Search: iterative-deepening negamax alpha-beta (PVS), transposition table,
  null move, late-move reductions, quiescence on captures.
- Order: TT move, killer move, then by material/PST gain (MVV-LVA-like).
- Eval: material plus piece-square tables, with endgame king and pawn tables.
- Fixed node budget per move, no clock, so the same position always gets the
  same move.

It plays every game through the env at `MAKEFUN_ENV_URL` (`/game`, `/move`).
