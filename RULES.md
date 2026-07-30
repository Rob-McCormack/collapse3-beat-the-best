# Rules in brief

*An abridgement for readers of [the exhibit](README.md). The canonical rulebook
is [`rules.md`](https://github.com/Rob-McCormack/collapse-3/blob/d422b3e/rules.md)
in the main repository; where the two differ, that one is right.*

Collapse3 is a two-player, perfect-information game on a 3×3 grid of nine
vertical pegs. Each peg holds up to three beads, giving 27 cells and **49
winning lines** — 9 vertical, 24 flat, and 16 staircase. Player 0 moves first,
and is the first entry in a reserve pair such as `(3,3)`.

Each player has a personal reserve of beads in their own colour — 14 each in the
full game. Beads stay in full view on their pegs, so every bead's owner is
visible even when buried under others. Smaller equal reserves such as `(3,3)` or
`(4,4)` are short variants, small enough to solve exactly. **These are reserve
counts, not board dimensions: the board never changes size.**

## On your turn, do exactly one of

**Place** one bead from your reserve onto any peg that is not full. It falls to
the lowest empty level.

**Collapse** — destroy one of the opponent's beads on a peg. This is permitted
only when all five conditions hold:

1. **Cooldown.** You did not collapse on your previous turn.
2. **Singleton immunity.** The peg holds at least two beads.
3. **Tallest stack.** The peg is tied for tallest on the board.
4. **Capping.** The topmost bead on that peg belongs to the opponent.
5. **Target.** The bead you take must be the opponent's — any of theirs on that
   peg, bottom, middle, or top, and never one of your own.

The bead is destroyed permanently, never returned to a reserve, and every bead
above it drops one level.

## Winning

Three of your own beads in a straight line wins immediately. A line may be
**vertical** (one peg), **flat** (a row, column, or diagonal at a single level),
or a **staircase** (three collinear pegs rising or falling one level per step).

Gravity is impartial: a collapse can complete a line for either player. If one
action completes lines for both, the player who moved wins. If it completes a
line only for your opponent, your opponent wins — the **"Oops" rule**.

## Ending otherwise

The game ends by attrition — most beads left on the board wins, equal counts
draw — when **either** both reserves are empty, **or** the player to move has no
legal action.

Both conditions matter, and the second is easy to miss. A player can run out of
moves while the opponent still holds beads in reserve: spend your last bead,
collapse on the following turn, and then cooldown blocks the collapse while the
empty reserve blocks the placement, leaving no legal action at all.

## Why the short games are the interesting ones

Under perfect play, equal reserves are a **draw from `(1,1)` through `(5,5)`**
and a **first-player win from `(6,6)` up**, including the full `(14,14)` game.
The short equal-reserve games are therefore the fair ones, which is why the
exhibit's results live at `(3,3)`, `(4,4)` and `(5,5)`. They are also the sizes
a computer can solve outright.
