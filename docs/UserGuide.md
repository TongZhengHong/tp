# ChessMaster User Guide

## Introduction

ChessMasterCLI is a command-line interface (CLI) chess game designed to make learning and training accessible for beginners while offering an engaging experience for all skill levels. This sleek and user-friendly chess simulator provides a platform for novice players to build their skills and understanding of the game.

- [Quick Start](#quick-start)
- [Starting a game](#starting-a-game)
- [Gameplay]()
- [Features](#features)
    - Gameplay features
        - [Make a move](#make-a-move)
        - [Show available moves: `moves`](#show-available-moves-moves)
        - [Show current chess board: `show`](#show-current-chess-board-show)
    - Getting help
        - [Show chess rules: `rules`](#show-chess-rules-rules)
        - [Show commands: `help`](#show-commands-help)
        - [Legend: `legend`](#view-pieces-representation-legend)
        - [Restart game: `restart`](#start-a-new-game-of-chess-restart)        
        - [View history of game moves: `history`](#view-history-of-all-game-moves-history)
        - [Step back in history: `stepback`](#step-back-in-history-stepback)
        - [List pieces in play: `captured`](#list-pieces-in-play-captured)
        - [Exit game: `exit`](#exit-the-game-exit)
- [Command Summary](#command-summary)

## Quick Start

1. Ensure you have **Java 11 or above** installed in your system.

2. Download the latest version of `ChessMaster.jar` from [here](https://github.com/AY2324S1-CS2113-T18-1/tp/releases).

3. Open a terminal instance and navigate into the folder that contains the downloaded ChessMaster.jar file.

```bash
cd PATH_TO_JAR_FILE
```

4. Run the jar application with the following command:

```bash
java -jar ChessMaster.jar
```

You should be greeted by a welcome message from ChessMaster:
```
_________________________________________________________________

Hey there, chess geek! You have stumbled upon the one and only:
    ________                      __  ___           __
   / ____/ /_  ___  __________   /  |/  /___ ______/ /____  _____
  / /   / __ \/ _ \/ ___/ ___/  / /|_/ / __ `/ ___/ __/ _ \/ ___/
 / /___/ / / /  __(__  |__  )  / /  / / /_/ (__  ) /_/  __/ /
 \____/_/ /_/\___/____/____/  /_/  /_/\__,_/____/\__/\___/_/

where CHESS becomes an exciting journey of strategy and skill!
_________________________________________________________________
```

## Starting a game

Upon launching the application, ChessMaster checks if there is a previous game in progress. If a previous game exists, you'll be presented with the option to continue from where you left off. Please enter `y` for **yes** and `n` for **no**.

```
You have an ongoing previous chess game. Continue game? [y/n/exit]
```

However, if you prefer to **start a fresh game** or if **no previous game is found**, ChessMaster will prompt you to select your preferred color—whether it's "White" or "Black." Please enter `b` for **black** and `w` for **white**.

```
Choose your starting color to start new game! [b/w/exit]
```

Next, you can choose the difficulty of the AI you will be pitched against! The current supported difficulty levels range from 1 to 4. Please enter the number corresponding to your preferred difficulty level.
```
Choose your difficulty level! [1/2/3/4/exit]
```

Inputs that are not compliant with the expect input (indicated in `[]`) will be rejected and users will be prompted to re-input.
Else, you'll be off to a rewarding journey of enhancing your chess skills and enjoying the timeless game of strategy and tactics with ChessMaster!

## Gameplay

The gameplay system of ChessMaster provides you with the flexibility to enter either a **command** or a **move** during your turn. 

- If you opt for a **command**, the system will promptly solicit your next action, allowing you to access various [features](#features) seamlessly. However, when you decide to make a move, the system will evaluate your input for validity. 
- Only when you enter a **valid move** will your turn be passed to the CPU, enabling it to respond with its strategic move. 

Additionally, every time a move is executed, ChessMaster provides a comprehensive view of the chessboard, displaying the state of the game following the previous move.

<table>
<tr>
    <th>User Move</th>
    <th>CPU move</th>
</tr>
<tr>
<td>

<pre><code>
move d2 d4
_________________________________________________________________

You moved Pawn from d2 to d4
_________________________________________________________________

                 (a) (b) (c) (d) (e) (f) (g) (h)
                _________________________________
            (8) | R | N | B | Q | K | B | N | R | (8)
                _________________________________
            (7) | P | P | P | P | P | P | P | P | (7)
                _________________________________
            (6) |   |   |   |   |   |   |   |   | (6)
                _________________________________
            (5) |   |   |   |   |   |   |   |   | (5)
                _________________________________
            (4) |   |   |   |(p)|   |   |   |   | (4)
                _________________________________
            (3) |   |   |   |   |   |   |   |   | (3)
                _________________________________
            (2) | p | p | p |( )| p | p | p | p | (2)
                _________________________________
            (1) | r | n | b | q | k | b | n | r | (1)
                _________________________________
                 (a) (b) (c) (d) (e) (f) (g) (h)
</code></pre>

</td>
<td>

<pre><code>
ChessMaster is thinking of a move...
_________________________________________________________________

ChessMaster moved Pawn from e7 to e5
_________________________________________________________________

                 (a) (b) (c) (d) (e) (f) (g) (h)
                _________________________________
            (8) | R | N | B | Q | K | B | N | R | (8)
                _________________________________
            (7) | P | P | P | P |( )| P | P | P | (7)
                _________________________________
            (6) |   |   |   |   |   |   |   |   | (6)
                _________________________________
            (5) |   |   |   |   |(P)|   |   |   | (5)
                _________________________________
            (4) |   |   |   | p |   |   |   |   | (4)
                _________________________________
            (3) |   |   |   |   |   |   |   |   | (3)
                _________________________________
            (2) | p | p | p |   | p | p | p | p | (2)
                _________________________________
            (1) | r | n | b | q | k | b | n | r | (1)
                _________________________________
                 (a) (b) (c) (d) (e) (f) (g) (h)
</code></pre>

</td>
</tr>
</table>

## Ending the game

The game will automatically end and a victor be declared when one side has been checkmated, or if both players are stuck in a stalemate situation where neither player can avoid moving into a checked position.

Checkmate is the point in the game where the attacking player has the opponent's king in a situation where it can't escape being captured on the next move.

The king is "trapped" and has no safe squares to move to, and no other pieces can help.

Otherwise, you may use the `exit` command if you wish to end the game midway and quit the program or `restart` command to start a new game. 

## Features 

### Make a move

To make a move, simply enter the coordinate of the piece to be moved, followed by the coordinates it is to be moved to.

Format: `move [column][row] [column][row]`

Examples: 
- `move a2 a4`
- `move b3 g6`

ChessMaster also automatically checks if the move was valid and legal before it is executed. If the move is valid, an output as shown above in the [Gameplay](#gameplay) section will be output. Else, the following error
message will be shown:

`Oops, that move isn't valid!`


### Show available moves: `moves`

Shows the available moves for a piece on the board. This command can be used for both yours and the enemy's pieces.

Format: `moves [column][row]`

Example:  `moves e5`

Expected Output:
```
                 (a) (b) (c) (d) (e) (f) (g) (h)
                _________________________________
            (8) | R | N | B | Q | K | B | N | R | (8)
                _________________________________
            (7) | P | P | P |[ ]|   |[P]| P | P | (7)
                _________________________________
            (6) |   |   |[ ]| P |   |   |[ ]|   | (6)
                _________________________________
            (5) |   |   |   |   |{n}|   |   |   | (5)
                _________________________________
            (4) |   |   |[ ]|   |   |   |[ ]|   | (4)
                _________________________________
            (3) |   |   |   |[ ]|   |[ ]|   |   | (3)
                _________________________________
            (2) | p | p | p | p | p | p | p | p | (2)
                _________________________________
            (1) | r | n | b | q | k | b |   | r | (1)
                _________________________________
                 (a) (b) (c) (d) (e) (f) (g) (h)

_________________________________________________________________

Available coordinates for Knight at e5: 
f7 d7 f3 d3 g6 g4 c6 c4 
_________________________________________________________________
```

### Show current chess board: `show`

Shows the current state of the chess board.

Format: `show`

Expected Output:

```
_________________________________________________________________

Here is the current board state:
_________________________________________________________________

                 (a) (b) (c) (d) (e) (f) (g) (h)
                _________________________________
            (8) | R | N | B | Q | K | B | N | R | (8)
                _________________________________
            (7) | P | P | P | P | P | P | P | P | (7)
                _________________________________
            (6) |   |   |   |   |   |   |   |   | (6)
                _________________________________
            (5) |   |   |   |   |   |   |   |   | (5)
                _________________________________
            (4) |   |   |   |   |   |   |   |   | (4)
                _________________________________
            (3) |   |   |   |   |   |   |   |   | (3)
                _________________________________
            (2) | p | p | p | p | p | p | p | p | (2)
                _________________________________
            (1) | r | n | b | q | k | b | n | r | (1)
                _________________________________
                 (a) (b) (c) (d) (e) (f) (g) (h)
                 
```

### Show chess rules: `rules`

Obtain a quick refresher on the rules of chess

Format: `rules`

Expected Output:
```
_________________________________________________________________

Here are simple chess rules to get you started:

Piece movement:
   Pawn ("p") move forward one square but capture diagonally.
   Rooks ("r") move horizontally and vertically any number of squares.
   Knights ("n") move in an L-shape.
   Bishops ("b") move diagonally any number of squares.
   Queens ("q") move any number of squares in any direction.
   Kings ("k") move one square in any direction.

Special Rules:
[Refer to specific move methods in the User Guide]
   Castling - King and rook move simultaneously to safeguard the king.
   En Passant - Pawn capturing when moving two squares from starting position.
   Pawn Promotion - Promote a pawn to another piece (except king) upon reaching the back rank.

Objective:
   Game ends when one player's king is in checkmate, under attack and can't escape capture.
   The delivering player wins the game.
_________________________________________________________________
```

#### 1. Castling

For the move to be valid:
- It's the king's first move. 
- It's the rook's first move. 
- There are no pieces between the king and the rook. 
- The king is not in check and the king will not be in check after castling

To perform castling on either sides:
- Move your king two squares to the right/left (towards the rook).
- The rook will jump over the king and land on the square next to the king.

Examples and expected output:

<table>
<tr>
    <th>Castling availability: <code>moves e1</code></th>
    <th>Execute castle move: <code>moves e1 c1</code></th>
</tr>
<tr>
<td>

<pre><code>             (a) (b) (c) (d) (e) (f) (g) (h)
            _________________________________
        (8) | R |   |   |   | K |   |   | R | (8)
            _________________________________
        (7) | P | P | P |   |   |   | P | P | (7)
            _________________________________
        (6) |   |   |   |   |   |   |   |   | (6)
            _________________________________
        (5) |   |   | q |   |   | P |   |   | (5)
            _________________________________
        (4) |   |   |   |   |   | p |   |   | (4)
            _________________________________
        (3) |   |   | n |   |   |   |   |   | (3)
            _________________________________
        (2) | B | p |   |[.]|[.]| p | p | p | (2)
            _________________________________
        (1) | r |   |[.]|[.]|{k}| b | n | r | (1)
            _________________________________
             (a) (b) (c) (d) (e) (f) (g) (h)

_________________________________________________________________

Available coordinates for King at e1:
e2 d1 d2 c1
_________________________________________________________________</code></pre>

</td>
<td>

<pre><code>_________________________________________________________________

You moved King from e1 to c1
_________________________________________________________________

             (a) (b) (c) (d) (e) (f) (g) (h)
            _________________________________
        (8) | R |   |   |   | K |   |   | R | (8)
            _________________________________
        (7) | P | P | P |   |   |   | P | P | (7)
            _________________________________
        (6) |   |   |   |   |   |   |   |   | (6)
            _________________________________
        (5) |   |   | q |   |   | P |   |   | (5)
            _________________________________
        (4) |   |   |   |   |   | p |   |   | (4)
            _________________________________
        (3) |   |   | n |   |   |   |   |   | (3)
            _________________________________
        (2) | B | p |   |   |   | p | p | p | (2)
            _________________________________
        (1) |   |   |(k)| r |( )| b | n | r | (1)
            _________________________________
             (a) (b) (c) (d) (e) (f) (g) (h)</code></pre>

</td>
</tr>
</table>

#### 2. En Passant:
   
This move only happens when your opponent moves their pawn two squares forward from its starting position and lands next to your pawn.
To capture en passant, you must do it on your very next move. 
- Move your pawn diagonally forward to the square that your opponent's pawn would have occupied if it had moved only one square forward.

<table>
<tr>
    <th>Sample board before en passant</th>
    <th>Executing en passant move: <code>move d5 e6</code></th>
</tr>
<tr>
<td>

<pre><code>_________________________________________________________________

ChessMaster moved Pawn from e7 to e5
_________________________________________________________________

             (a) (b) (c) (d) (e) (f) (g) (h)
            _________________________________
        (8) | R |   | B | Q | K | B |   | R | (8)
            _________________________________
        (7) | P | P | P | P |( )| P | P | P | (7)
            _________________________________
        (6) |   |   | N |   |   |   |   |   | (6)
            _________________________________
        (5) |   |   |   | p |(P)|   |   |   | (5)
            _________________________________
        (4) |   |   |   |   |   |   |   |   | (4)
            _________________________________
        (3) |   |   |   |   |   |   |   |   | (3)
            _________________________________
        (2) | p | p |   |   | p | p | p | p | (2)
            _________________________________
        (1) | r | n | b | q | k | b | n | r | (1)
            _________________________________
             (a) (b) (c) (d) (e) (f) (g) (h)</code></pre>

</td>
<td>

<pre><code>
             (a) (b) (c) (d) (e) (f) (g) (h)
            _________________________________
        (8) | R |   | B | Q | K | B |   | R | (8)
            _________________________________
        (7) | P | P | P | P |   | P | P | P | (7)
            _________________________________
        (6) |   |   | N |   |(p)|   |   |   | (6)
            _________________________________
        (5) |   |   |   |( )|   |   |   |   | (5)
            _________________________________
        (4) |   |   |   |   |   |   |   |   | (4)
            _________________________________
        (3) |   |   |   |   |   |   |   |   | (3)
            _________________________________
        (2) | p | p |   |   | p | p | p | p | (2)
            _________________________________
        (1) | r | n | b | q | k | b | n | r | (1)
            _________________________________
             (a) (b) (c) (d) (e) (f) (g) (h)</code></pre>

</td>
</tr>
</table>

### Show commands: `help`

Show a list of commands and what they do

Format: `help`

Expected Output:

```
_________________________________________________________________

Here are the commands you can use to play:
move		Move piece
		Format: move [column][row] [column][row]
		e.g. move a2 a3
moves		Show available moves for a piece
		Format: moves [column][row]
		e.g. moves a2
show		Show the chessboard
rules		Obtain a quick refresher on the rules of chess
legend		View pieces representation
restart		Start a new game
history		View history of all game moves
stepback	View the board as it was a certain number of moves ago
		Format: stepback [number of moves to step back]
		e.g. stepback 4
captured	See which Player and CPU pieces have been captured so far
exit		Exit game
_________________________________________________________________
```


### View pieces representation: `legend` 

Display a legend that explains the piece representations

Format: `legend`

Expected Output:

```
_________________________________________________________________

Black pieces:
"R" represents a black rook.
"N" represents a black knight.
"B" represents a black bishop.
"Q" represents a black queen.
"K" represents a black king.
"P" represents a black pawn.
   
White pieces:
"r" represents a white rook.
"n" represents a white knight.
"b" represents a white bishop.
"q" represents a white queen.
"k" represents a white king.
"p" represents a white pawn.
_________________________________________________________________
```

### Start a new game of chess: `restart`

Enables the player to restart the game.
Selecting `y` will restart the game, while `n` will cause player to exit program.

Format: `restart`

Expected output:

```
Do you want to restart game? [y/n] 
```

### View history of all game moves: `history`

Displays a list of all previous moves in the current game

Format: `history`

Sample output:
```
_________________________________________________________________

Move 1: WHITE moves Knight from g8 to f6
Move 2: BLACK moves Pawn from a2 to a4
Move 3: WHITE moves Knight from b8 to c6

_________________________________________________________________
```

### Step back in history: `stepback`

Displays the board state as it was a certain number of moves ago. Note that this command does not reverse any moves
in the current game.

Format: `stepback [number of moves to step back]`

Example: `stepback 2`

Sample output:

```
                (a) (b) (c) (d) (e) (f) (g) (h)
                _________________________________
            (8) | r | n | b | q | k | b |   | r | (8)
                _________________________________
            (7) | p | p | p | p | p | p | p | p | (7)
                _________________________________
            (6) |   |   |   |   |   | n |   |   | (6)
                _________________________________
            (5) |   |   |   |   |   |   |   |   | (5)
                _________________________________
            (4) |   |   |   |   |   |   |   |   | (4)
                _________________________________
            (3) |   |   |   |   |   |   |   |   | (3)
                _________________________________
            (2) | P | P | P | P | P | P | P | P | (2)
                _________________________________
            (1) | R | N | B | Q | K | B | N | R | (1)
                _________________________________
                (a) (b) (c) (d) (e) (f) (g) (h)

_________________________________________________________________

Stepped back 2 steps!
Use `show` to see the current board.
_________________________________________________________________
```

### List pieces in play: `captured`

Lists each player's pieces grouped by whether they have been captured or not.

Format: `captured`

Sample output:

```
_________________________________________________________________

Player's pieces
----------------------------------------
In play:
- Bishop x2
- King
- Knight
- Pawn x7
- Rook x2

Captured:
- Queen
- Knight
- Pawn


CPU's pieces
----------------------------------------

In play:
- Bishop x2
- King
- Queen
- Knight
- Pawn x7
- Rook x2

Captured:
- Knight
- Pawn

_________________________________________________________________

```

### Exit the game: `exit`

Exit the ChessMaster application.

Format: `exit`

Expected Output:

```
_________________________________________________________________

Exiting program... Thanks for playing!
_________________________________________________________________
```

### Saving and loading games

Every time a turn ends, ChessMaster will save the current state of the game. When ChessMaster is restarted, the
user will be prompted to choose whether to load the saved game or begin a new one. ChessMaster only supports a single
saved game, and starting a new one will delete the existing save file.

## FAQ

> **Q**: How do I transfer my data to another computer? 

**A**: You can navigate to your root folder, and find the file `data/ChessMaster.txt`. Transfer the file to your other computer,
and find the `data` folder in the ChessMaster install folder in the other computer. Copy the file into the folder. Start ChessMaster,
and type `y` when prompted to load a saved game.

> **Q**: How do I play with another person?

**A**: Currently, ChessMaster does not support multiplayer. 

> **Q**: Can we play timed games?

**A**: ChessMaster does not come with an internal timer. However, you are able to use your own chess timer or stopwatch to simulate timed games.

> **Q**: Can I draw by repeating moves?

**A**: ChessMaster does not currently support draws by repetition. However, you can use the `exit` command to end the game. Alternatively, you can maneuver the game to a draw by stalemate, where neither party can move without being in check or there are only kings left on the board.

## Command Summary

| Action               | Format                             |
|----------------------|------------------------------------|
| Move                 | `move [column][row] [column][row]` |
| Show moves           | `moves [column][row]`              |
| Show board           | `show`                             |
| Rules                | `rules`                            |
| Help                 | `help`                             |
| Pieces legend        | `legend`                           |
| Restart game         | `restart`                          |
| History              | `history`                          |
| Step back            | `stepback [number of steps]`       |
| List captured pieces | `captured`                         |
| Exit                 | `exit`                             |

