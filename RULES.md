# Rules in brief

*An abridgement for readers of [the exhibit](README.md). The canonical rulebook
is [`rules.md`](https://github.com/Rob-McCormack/collapse-3/blob/d422b3e/rules.md)
in the main repository; where the two differ, that one is right.*

## Before the rules: what is strange here?

Collapse3 uses a familiar 3×3×3 board, but play is driven by placement,
destruction and gravity. The game is deterministic and perfect-information, yet
the visible board is not the whole position. Reserves and cooldown can give
identical-looking boards different legal futures, so the game is temporal as
much as spatial.

**Ownership is fixed; control is not.** You choose where a bead enters, but only
your opponent can destroy it, and either player's collapse can drop it into a
line it was never placed in. You can check the shape of this against the rules
in one step: a removal requires the target peg's top bead to belong to your
opponent, and placements always land on top — so topping a peg satisfies your
opponent's attack condition rather than defending it. A bead can turn from
threat into support, shield, cap or liability without its owner moving.

**Positions are co-authored, and your own move can lose.** A collapse edits both
players' structures. It can complete your opponent's line and end the game on
your turn.

**Even a mistake can be an attack.** An objectively worse move can expose a
weakness that perfect play never reaches. The strongest player is not the
strongest tester.

**Solved is not understood.** The solver certifies the correct move without
explaining why. Exact solutions have not yet produced a basic strategy that
holds as reserves grow — a game an eight-year-old can learn in two minutes,
with no known strategy that scales. What solving provides is ground truth:
these shifting meanings become measurable.

## The board and the reserves

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

Both conditions matter, and the second is easy to miss. Once your reserve is
empty, a collapse is always your final action: cooldown blocks the removal on
your next turn and the empty reserve blocks the placement, so you have no legal
action and the game ends on bead count — whatever your opponent does in
between. A player can therefore run out of moves while the opponent still holds
beads in reserve.

## Why the short games are the interesting ones

Under perfect play, equal reserves are a **draw from `(1,1)` through `(5,5)`**
and a **first-player win from `(6,6)` up**, including the full `(14,14)` game.
The short equal-reserve games are therefore the fair ones, which is why the
exhibit's results live at `(3,3)`, `(4,4)` and `(5,5)`. They are also the sizes
a computer can solve outright.
