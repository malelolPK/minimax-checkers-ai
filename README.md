# Checkers with Minimax & Alpha-Beta AI

Checkers game implementation with Minimax and Alpha-Beta pruning algorithms in Godot Engine 4.1. Player vs AI with configurable search depth (4-7 levels).

## Features

- **Two AI algorithms**: Minimax and Alpha-Beta Pruning
- **Complete checkers rules**: Standard moves, kings, multi-jumps, forced captures
- **Configurable search depth**: 4-5 levels (can handle up to 7 with Alpha-Beta)
- **Evaluation function**: Material count, center control, mobility, king proximity
- **UI**: Menu system, move visualization, sound effects

## Tech Stack

- **Engine**: Godot 4.1
- **Language**: GDScript
- **Patterns**: Singleton, Strategy
- **Architecture**: Modular scene-based design

## Project Structure

```
ai-checkers/
├── main.gd                          # Game controller (646 lines)
├── main.tscn                        # Main scene
├── project.godot                    # Godot config
│
├── asset/
│   ├── AI/
│   │   ├── AIMiniMax.gd            # Minimax implementation (379 lines)
│   │   ├── AIAlphaBeta.gd          # Alpha-Beta pruning (453 lines)
│   │   ├── white.tscn / black.tscn # Pawn scenes
│   │   └── white_king.tscn / black_king.tscn # King scenes
│   │
│   ├── Board/
│   │   └── GameState.gd            # Game state for simulation
│   │
│   ├── FUNKCJE LOGIKI GRY/
│   │   ├── PawnMovement.gd         # Move generation (271 lines)
│   │   ├── AttackMoves.gd          # Capture detection (257 lines)
│   │   └── game_over.gd/tscn       # Game over screen
│   │
│   ├── main_menu/
│   │   ├── main_menu.gd/tscn       # Main menu
│   │   └── select_menu.gd/tscn     # Algorithm selection
│   │
│   ├── Singleton/
│   │   └── GlobalVariables.gd      # Global state (singleton pattern)
│   │
│   └── sound/
│       ├── ruch pionka.MP3         # Move sound
│       ├── zbicie.MP3              # Capture sound
│       └── game_over.MP3           # Game over sound
```

## AI Implementation

### Minimax (`AIMiniMax.gd`)

Classic recursive game tree search algorithm.

**Core functions:**
```gdscript
func findBestMove(_board, targetDepth, TYPE, _previousTurnWasAttack, _previousPawnAttack)
    # Searches all possible moves for all pawns
    # Calls Minimax() recursively for each move

func Minimax(game_state, curDepth, targetDepth, isMaximizingPlayer)
    # Recursive minimax with alternating max/min layers
    # Returns evaluation score from evaluate()

func evaluate(game_state)
    # Simple evaluation: pawn = ±1, king = ±10, win = ±10000
```

**Features:**
- First move randomization for variety
- Board state duplication for simulation
- Multi-jump support via `previousTurnWasAttack`

### Alpha-Beta Pruning (`AIAlphaBeta.gd`)

Optimized minimax with branch pruning.

**Core functions:**
```gdscript
func find_best_move(_board, _targetDepth, TYPE, _previousTurnWasAttack, _previousPawnAttack)
    # Initializes alpha=-∞, beta=+∞

func AlphaBeta(game_state, depth, isMax, alpha, beta)
    # Prunes branches when alpha >= beta
    # Same result as Minimax, but 10-100× faster

func evaluate_complicated(game_state)
    # Advanced evaluation considering:
    # - Material: pawns (×2), kings (×10)
    # - Center control: +2 per center position
    # - King proximity: +2 when close to promotion
    # - Edge control: +2 for edge positions
    # - Mobility: points per available move
```

**Formula:**
```gdscript
score = (sum_piece * 2 + (3 * sum_kings)) * 10 
        + sum_central_control * 2 
        + sum_close_to_be_king * 2 
        + sum_control_edge_left_right * 2 
        + sum_mobility_pawns / 4
```

**Performance:**
- Minimax depth 5: ~2-5 seconds
- Alpha-Beta depth 7: ~0.5-1 second
- Time complexity: O(b^d) → O(b^(d/2)) best case

### Game Logic

**Move Generation (`PawnMovement.gd`):**
```gdscript
func all_possible_move_types_pawn(_TYPE_PAWN: String, _board: Array) -> Dictionary
    # Returns {pawn_reference: [array_of_moves]}

func possible_move_pawn(pawn, _board: Array) -> Array
    # Standard diagonal moves, forward/backward captures

func possible_move_pawn_king(pawn, _board: Array) -> Array
    # Kings move in all 4 diagonal directions
```

**Capture Detection (`AttackMoves.gd`):**
```gdscript
func is_attack_move_available_for_type(_TYPE_PAWN: String, _board: Array)
    # Sets GlobalVariables.is_attack flag

func check_attack_move(row, col, directionRow, directionCol, pionek, _board)
    # Low-level capture validation
```

**State Management (`GameState.gd`):**
```gdscript
class_name GameState
    var board: Array
    var previousTurnWasAttackGameState: bool
    var previousPawnAttackGameState: String
    var curretDepth: int
    var nonCaptureMoveCount: int
    var created_king: bool
```

Used for board state simulation in AI algorithms without modifying real board.

## Installation

**Requirements:**
- Godot Engine 4.1+
- 2GB RAM minimum

**Option 1: From source**
```bash
git clone https://github.com/malelolPK/ai-checkers.git
cd ai-checkers
godot --path . --editor  # Press F5 to run
```

**Option 2: Import to Godot**
1. Open Godot Engine
2. Click "Import" → select `project.godot`
3. Press F5

**Configure AI search depth** in `main.gd`:
```gdscript
# Minimax (4-5 recommended)
var best_move = ai_script_mini_max.findBestMove(
    GlobalVariables.board, 
    5,  # depth: 3=fast/weak, 5=balanced, 7=slow/strong
    "black", 
    previousTurnWasAttack, 
    previousPawnAttack
)

# Alpha-Beta (6-8 recommended)
var best_move = ai_script_alpha_beta.find_best_move(
    GlobalVariables.board, 
    7,  # Alpha-Beta handles 6-8 efficiently
    "black", 
    previousTurnWasAttack, 
    previousPawnAttack
)
```

## How to Play

**Rules:**
- Standard checkers rules (diagonal moves, forced captures, kings)
- Left-click to select pawn and make move
- Possible moves highlighted automatically
- Win by capturing all opponent pieces or blocking their moves

**Gameplay:**

![Player move](./asset/screenshots/gameplay_player.gif)
![AI response](./asset/screenshots/gameplay_ai.gif)

## Algorithm Comparison

| Metric | Minimax | Alpha-Beta |
|--------|---------|------------|
| Time complexity | O(b^d) | O(b^(d/2)) best case |
| Practical depth | 4-5 | 6-8 |
| Time (depth 5) | ~2-5 sec | ~0.5-1 sec |
| Speedup | 1× | 10-100× |

*b = branching factor (~7 moves avg), d = search depth*

## License

MIT License

## Author

**GitHub**: [@malelolPK](https://github.com/malelolPK)
