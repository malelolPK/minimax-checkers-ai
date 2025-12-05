# 🎮 AI Checkers Game - Warcaby z algorytmami Minimax i Alpha-Beta

> Zaawansowana implementacja gry w warcaby (checkers) z wykorzystaniem algorytmów sztucznej inteligencji w silniku Godot Engine 4.1

[![Godot Engine](https://img.shields.io/badge/Godot-4.1-blue.svg)](https://godotengine.org/)
[![GDScript](https://img.shields.io/badge/GDScript-100%25-green.svg)](https://docs.godotengine.org/en/stable/tutorials/scripting/gdscript/index.html)
[![License](https://img.shields.io/badge/license-MIT-orange.svg)](LICENSE)

---

## 📋 Executive Summary

**AI Checkers** to w pełni funkcjonalna gra w warcaby z zaawansowanym systemem sztucznej inteligencji opartym na klasycznych algorytmach teorii gier. Projekt demonstruje głęboką znajomość algorytmów AI, programowania gier oraz architektury oprogramowania.

Gra pozwala na rozgrywkę człowieka przeciwko komputerowi, który wykorzystuje dwa różne algorytmy AI:
- **Minimax** - klasyczny algorytm przeszukiwania drzewa gry z konfigurowalna głębokością
- **Alpha-Beta Pruning** - zoptymalizowana wersja Minimax z przycinaniem drzewa decyzyjnego

Projekt zawiera kompletną logikę gry w warcaby, w tym:
- Ruchy standardowe i damki (kings)
- System bić wielokrotnych
- Promocje pionków do damek
- Detekcję końca gry i warunków zwycięstwa
- System menu i interfejs użytkownika

---

## ✨ Key Features

### 🤖 Sztuczna Inteligencja
- **Dwa algorytmy AI** do wyboru: Minimax i Alpha-Beta Pruning
- **Konfigurowalna głębokość przeszukiwania** (depth 4-5 widoczne w eksportach)
- **Zaawansowana funkcja ewaluacji** uwzględniająca:
  - Liczbę i rodzaj pionków
  - Kontrolę centrum planszy
  - Mobilność pionków
  - Bliskość promocji do damki
  - Kontrolę krawędzi planszy

### 🎲 Mechanika Gry
- **Pełne zasady polskich/międzynarodowych warcabów**
- **System bić obowiązkowych** z detekcją możliwości ataku
- **Bicia wielokrotne** w jednej turze
- **Promocja do damki** przy osiągnięciu końca planszy
- **Ruch damek** we wszystkich kierunkach po przekątnej
- **Detekcja remisu** (brak bić przez określoną liczbę ruchów)

### 🎨 Interfejs i UX
- **System menu** z wyborem algorytmu AI
- **Wizualizacja możliwych ruchów**
- **Animacje ruchów pionków**
- **Efekty dźwiękowe** (ruch pionka, bicie, koniec gry)
- **Interfejs 1000x800px** z planszą 8x8

### 🏗️ Architektura
- **Modułowa struktura kodu** z separacją logiki
- **Singleton pattern** dla zmiennych globalnych
- **Scene-based architecture** w Godot
- **Klasa GameState** do symulacji stanów gry w algorytmach AI

---

## 🛠️ Tech Stack & Skills Demonstrated

### Technologie
| Kategoria | Technologia |
|-----------|-------------|
| **Game Engine** | Godot Engine 4.1 |
| **Język** | GDScript |
| **Architektura** | OOP, Scene Tree, Singleton Pattern |
| **Export** | Standalone `.pck` files |

### Umiejętności programistyczne
- ✅ **Algorytmy AI** - implementacja Minimax i Alpha-Beta Pruning
- ✅ **Teoria gier** - funkcje ewaluacji, przeszukiwanie drzewa gry, heurystyki
- ✅ **Programowanie obiektowe** - klasy, dziedziczenie, enkapsulacja
- ✅ **Struktury danych** - tablice 2D, słowniki, grafy (drzewo gry)
- ✅ **Architektura oprogramowania** - modularność, separation of concerns
- ✅ **Game development** - game loop, state management, event handling
- ✅ **Debugging i optymalizacja** - zarządzanie wydajnością algorytmów

### Koncepcje teoretyczne
- **Minimax Algorithm** - rekurencyjne przeszukiwanie drzewa gry
- **Alpha-Beta Pruning** - optymalizacja przez eliminację nieperspektywicznych gałęzi
- **Game State Evaluation** - heurystyczna ocena pozycji
- **Move Generation** - generowanie legalnych ruchów
- **Game Tree Search** - eksploracja przestrzeni stanów gry

---

## 📁 Project Structure & File Breakdown

```
ai-checkers/
├── main.gd                          # Główny kontroler gry
├── main.tscn                        # Główna scena gry
├── project.godot                    # Konfiguracja projektu Godot
│
├── asset/
│   ├── AI/
│   │   ├── AIMiniMax.gd            # Implementacja algorytmu Minimax
│   │   ├── AIAlphaBeta.gd          # Implementacja Alpha-Beta Pruning
│   │   ├── white.tscn              # Scena białego pionka
│   │   ├── black.tscn              # Scena czarnego pionka
│   │   ├── white_king.tscn         # Scena białej damki
│   │   └── black_king.tscn         # Scena czarnej damki
│   │
│   ├── Board/
│   │   └── GameState.gd            # Klasa reprezentująca stan gry
│   │
│   ├── FUNKCJE LOGIKI GRY/
│   │   ├── PawnMovement.gd         # Logika ruchów pionków
│   │   ├── AttackMoves.gd          # Logika bić i ataków
│   │   └── game_over.gd/tscn       # Ekran końca gry
│   │
│   ├── main_menu/
│   │   ├── main_menu.gd/tscn       # Menu główne
│   │   └── select_menu.gd/tscn     # Menu wyboru algorytmu AI
│   │
│   ├── Player/
│   │   └── pawn_move.tscn          # Wizualizacja możliwych ruchów
│   │
│   ├── Singleton/
│   │   └── GlobalVariables.gd      # Zmienne globalne (singleton)
│   │
│   ├── sound/
│   │   ├── ruch pionka.MP3         # Dźwięk ruchu
│   │   ├── zbicie.MP3              # Dźwięk bicia
│   │   └── game_over.MP3           # Dźwięk końca gry
│   │
│   └── UI/                          # Elementy interfejsu użytkownika
│
└── Eksporty gry:
    ├── Warcaby.pck                  # Podstawowa wersja
    ├── Warcaby Głębokością 4.pck    # AI z depth=4
    └── Warcaby Głębokością 5.pck    # AI z depth=5
```

---

## 🔍 Detailed File Descriptions

### 🎯 Core Game Logic

#### `main.gd` (646 linii)
**Główny kontroler gry - serce całej aplikacji**

**Odpowiedzialności:**
- Inicjalizacja planszy 8x8 i pionków
- Obsługa interakcji gracza (kliknięcia myszą)
- Zarządzanie turami (gracz vs AI)
- Wizualizacja ruchów i bić
- Promocja pionków do damek
- Detekcja końca gry

**Kluczowe zmienne:**
```gdscript
var GRIDSIZE: int = 8                    # Rozmiar planszy
var help_board: Array = []               # Tablica 2D reprezentująca stan planszy
var isPlayerTurn: bool = true            # Flaga tury gracza
var isAITurn: bool = false               # Flaga tury AI
var is_attack: bool = false              # Czy dostępne są bicia
var possible_move: Array = []            # Możliwe ruchy
var possible_attack: Array = []          # Możliwe bicia
```

**Kluczowe funkcje:**
- `initialize_game_state()` - inicjalizacja gry, ładowanie algorytmów AI
- `setup_initial_board_state()` - ustawienie początkowej pozycji pionków
- `promote_to_king()` - promocja pionków do damek
- `_input(event)` - obsługa kliknięć gracza
- AI turn handling - wykonywanie ruchów AI

---

### 🤖 AI Algorithms

#### `asset/AI/AIMiniMax.gd` (379 linii)
**Implementacja klasycznego algorytmu Minimax**

**Opis algorytmu:**
Minimax to algorytm przeszukiwania drzewa gry, który zakłada, że przeciwnik gra optymalnie. Algorytm eksploruje wszystkie możliwe ruchy do określonej głębokości i wybiera ruch maksymalizujący szansę wygranej (lub minimalizujący stratę).

**Kluczowe funkcje:**
```gdscript
func findBestMove(_board, targetDepth, TYPE, _previousTurnWasAttack, _previousPawnAttack)
```
- Główna funkcja znajdująca najlepszy ruch dla AI
- Przeszukuje wszystkie możliwe ruchy dla wszystkich pionków
- Wywołuje rekurencyjnie `Minimax()` dla każdego możliwego ruchu

```gdscript
func Minimax(game_state, curDepth, targetDepth, isMaximizingPlayer)
```
- Rekurencyjna implementacja algorytmu Minimax
- `isMaximizingPlayer` - true dla AI (maksymalizuje wynik), false dla gracza (minimalizuje)
- Warunek stopu: osiągnięcie głębokości lub koniec gry
- Zwraca ocenę pozycji z funkcji `evaluate()`

```gdscript
func evaluate(game_state)
```
- Funkcja oceny stanu planszy
- Przypisuje wartości punktowe:
  - Zwykły pionek: ±1 punkt
  - Damka: ±10 punktów
  - Zwycięstwo: ±10000 punktów

**Szczegóły implementacji:**
- Obsługa pierwszego ruchu - losowy wybór dla różnorodności gry
- Symulacja ruchów na kopii planszy (`game_state.board.duplicate(true)`)
- Obsługa bić wielokrotnych (poprzez `previousTurnWasAttack`)

---

#### `asset/AI/AIAlphaBeta.gd` (453 linie)
**Zoptymalizowana wersja Minimax z przycinaniem Alpha-Beta**

**Opis algorytmu:**
Alpha-Beta Pruning to optymalizacja Minimax, która przyspiesza przeszukiwanie przez eliminację gałęzi drzewa, które na pewno nie wpłyną na ostateczną decyzję. Osiąga to samo rozwiązanie jak Minimax, ale znacznie szybciej.

**Kluczowe funkcje:**
```gdscript
func find_best_move(_board, _targetDepth, TYPE, _previousTurnWasAttack, _previousPawnAttack)
```
- Analogiczna do Minimax, ale inicjalizuje parametry alpha i beta

```gdscript
func AlphaBeta(game_state, depth, isMax, alpha, beta)
```
- Rekurencyjna implementacja z przycinaniem
- `alpha` - najlepsza wartość dla maksymalizującego gracza
- `beta` - najlepsza wartość dla minimalizującego gracza
- Przycina gałęzie gdy `alpha >= beta`

```gdscript
func evaluate_complicated(game_state)
```
- **Zaawansowana funkcja ewaluacji** uwzględniająca wiele czynników:
  - **Materiał**: pionki (×2) i damki (×10)
  - **Kontrola centrum**: +2 punkty za pozycje środkowe
  - **Bliskość promocji**: +2 punkty gdy blisko końca planszy
  - **Kontrola krawędzi**: +2 punkty za pozycje na bokach
  - **Mobilność**: punkty za liczbę dostępnych ruchów

**Przykład obliczeń:**
```gdscript
score = (sum_piece * 2 + (3 * sum_kings)) * 10 
        + sum_central_control * 2 
        + sum_close_to_be_king * 2 
        + sum_control_edge_left_right * 2 
        + sum_mobility_pawns / 4
```

**Zalety Alpha-Beta vs Minimax:**
- ⚡ Średnio 10-100× szybsze przeszukiwanie
- 📊 Pozwala na większą głębokość przy tym samym czasie
- 🎯 Identyczne wyniki końcowe jak Minimax
- 🔧 Lepsza skalowalność

---

### 🎲 Game Logic

#### `asset/FUNKCJE LOGIKI GRY/PawnMovement.gd` (271 linii)
**Moduł odpowiedzialny za generowanie legalnych ruchów**

**Kluczowe funkcje:**

```gdscript
func all_possible_move_types_pawn(_TYPE_PAWN: String, _board: Array) -> Dictionary
```
- Generuje wszystkie możliwe ruchy dla wszystkich pionków danego koloru
- Zwraca słownik: `{pawn_reference: [array_of_moves]}`
- Rozróżnia zwykłe pionki i damki

```gdscript
func posibble_move_pawn(pawn, _board: Array) -> Array
```
- Generuje możliwe ruchy dla pojedynczego zwykłego pionka
- Uwzględnia kierunek (białe w górę, czarne w dół)
- Obsługuje:
  - Zwykłe ruchy po przekątnej
  - Bicia w przód
  - Bicia do tyłu (według zasad warcabów)

```gdscript
func possible_move_pawn_king(pawn, _board: Array) -> Array
```
- Generuje możliwe ruchy dla damki
- Damka może poruszać się we wszystkich 4 kierunkach po przekątnej
- Obsługuje bicia wielopolowe

```gdscript
func possible_diagonal_move(_row: int, _col: int, _board: Array) -> bool
func possible_diagonal_jump(_row: int, _col: int, directionRow: int, directionCol: int, _board: Array) -> bool
```
- Funkcje pomocnicze sprawdzające legalność ruchów
- Walidacja granic planszy
- Sprawdzanie kolizji z innymi pionkami

---

#### `asset/FUNKCJE LOGIKI GRY/AttackMoves.gd` (257 linii)
**Moduł zarządzania biciami i atakami**

**Odpowiedzialności:**
- Detekcja dostępności bić dla gracza/AI
- Implementacja zasady obowiązkowego bicia
- Sprawdzanie możliwości bić wielokrotnych

**Kluczowe funkcje:**

```gdscript
func is_attack_move_available_for_type(_TYPE_PAWN: String, _board: Array)
```
- Sprawdza czy dla danego koloru dostępne są jakiekolwiek bicia
- Ustawia globalną flagę `GlobalVariables.is_attack = true/false`
- Sprawdza zarówno zwykłe pionki jak i damki

```gdscript
func is_attack_move_available_pawn(PAWN, _board: Array) -> bool
```
- Sprawdza czy konkretny pionek ma dostępne bicia
- Używane dla bić wielokrotnych (ten sam pionek bije kolejny raz)

```gdscript
func check_attack_move(row: int, col: int, directionRow: int, directionCol: int, pionek: String, _board: Array) -> bool
```
- Niskopoziomowa funkcja sprawdzająca możliwość bicia
- Waliduje:
  - Czy pole jest w granicach planszy
  - Czy na polu jest pionek przeciwnika
  - Czy pole docelowe (za przeciwnikiem) jest puste

---

#### `asset/Board/GameState.gd` (19 linii)
**Klasa reprezentująca stan gry**

```gdscript
class_name GameState

var board: Array                              # Tablica 2D z referencjami do pionków
var previousTurnWasAttackGameState: bool      # Czy poprzedni ruch był biciem
var previousPawnAttackGameState: String       # Referencja do pionka, który bił
var curretDepth: int                          # Aktualna głębokość w drzewie przeszukiwania
var nonCaptureMoveCount: int                  # Licznik ruchów bez bicia (dla remisu)
var created_king: bool                        # Czy w tym ruchu powstała damka
var currect_turn_attack: bool                 # Czy aktualny ruch to bicie
var is_game_over: bool                        # Czy gra się zakończyła
```

**Zastosowanie:**
- Używana w algorytmach AI do symulacji ruchów
- Umożliwia "cofanie" ruchów bez modyfikacji prawdziwej planszy
- Każda symulacja tworzy nową instancję z `board.duplicate(true)`
- Przekazywana rekurencyjnie w drzewie przeszukiwania

---

### 🎨 UI & Menu System

#### `asset/main_menu/main_menu.gd` (18 linii)
**Menu główne gry**

```gdscript
func on_start_pressed() -> void:
    get_tree().change_scene_to_packed(start_level)

func on_exit_pressed() -> void:
    get_tree().quit()
```

#### `asset/main_menu/select_menu.gd` (22 linie)
**Menu wyboru algorytmu AI**

```gdscript
func minimax_pressed() -> void:
    get_tree().set_meta("algorithm_choice", 1)      # Wybór Minimax
    get_tree().change_scene_to_packed(start_level)

func alpha_beta_pressed() -> void:
    get_tree().set_meta("algorithm_choice", 2)      # Wybór Alpha-Beta
    get_tree().change_scene_to_packed(start_level)
```

**Przepływ aplikacji:**
1. Start → Main Menu
2. Wybór algorytmu → Select Menu
3. Ustawienie metadanych w drzewie scen
4. Załadowanie głównej sceny gry z wybranym algorytmem

---

### 🔧 Utilities

#### `asset/Singleton/GlobalVariables.gd` (12 linii)
**Singleton przechowujący zmienne globalne**

```gdscript
var board: Array = []              # Referencja do głównej planszy
var is_attack: bool = false        # Globalna flaga dostępności bić
var previousPawn: String = ""      # Pionek z poprzedniej tury (dla bić wielokrotnych)
```

**Zastosowanie Singleton Pattern:**
- Dostęp z każdego skryptu: `GlobalVariables.is_attack`
- Zarejestrowany w `project.godot` jako autoload
- Upraszcza komunikację między modułami

---

## 🏛️ Architecture Overview

### Architektura wysokiego poziomu

```
┌─────────────────────────────────────────────────────────────┐
│                        MAIN GAME LOOP                       │
│                        (main.gd)                            │
└────────────────────────┬────────────────────────────────────┘
                         │
          ┌──────────────┼──────────────┐
          │              │              │
          ▼              ▼              ▼
    ┌─────────┐    ┌─────────┐   ┌──────────┐
    │  PLAYER │    │   AI    │   │   BOARD  │
    │  INPUT  │    │ ENGINE  │   │  STATE   │
    └─────────┘    └─────────┘   └──────────┘
          │              │              │
          │        ┌─────┴─────┐        │
          │        │           │        │
          ▼        ▼           ▼        ▼
    ┌─────────────────────────────────────┐
    │         GAME LOGIC LAYER            │
    │  - PawnMovement                     │
    │  - AttackMoves                      │
    │  - GameState                        │
    └─────────────────────────────────────┘
                     │
                     ▼
          ┌──────────────────────┐
          │  GLOBAL VARIABLES    │
          │    (Singleton)       │
          └──────────────────────┘
```

### Przepływ danych w turze AI

```
1. MAIN (isAITurn = true)
   │
   ├─→ Wybór algorytmu (Minimax / Alpha-Beta)
   │
2. AI Algorithm::findBestMove()
   │
   ├─→ PawnMovement.all_possible_move_types_pawn()
   │   └─→ Generuje wszystkie możliwe ruchy
   │
   ├─→ Dla każdego ruchu:
   │   ├─→ Tworzy GameState (symulacja)
   │   ├─→ ai_make_move() (wykonuje ruch w symulacji)
   │   ├─→ Wywołuje Minimax/AlphaBeta (rekurencyjnie)
   │   │   ├─→ evaluate() / evaluate_complicated()
   │   │   └─→ Zwraca score
   │   └─→ Porównuje scores i wybiera najlepszy
   │
3. Zwraca [pawn, move]
   │
4. MAIN wykonuje ruch na prawdziwej planszy
   │
5. Zmiana tury → isPlayerTurn = true
```

### Pattern Design użyte w projekcie

1. **Singleton Pattern** - `GlobalVariables.gd`
   - Jeden globalny dostęp do stanu gry

2. **Strategy Pattern** - Wymienne algorytmy AI
   - `AIMiniMax.gd` i `AIAlphaBeta.gd` implementują tę samą funkcjonalność
   - Wybór algorytmu w runtime

3. **State Pattern** - Zarządzanie turami
   - `isPlayerTurn` / `isAITurn` przełączają stan gry

4. **Module Pattern** - Separacja logiki
   - `PawnMovement`, `AttackMoves` jako niezależne moduły

---

## 🚀 Installation & Setup

### Wymagania systemowe

```
✓ Godot Engine 4.1 lub nowszy
✓ System: Windows / Linux / macOS
✓ Pamięć RAM: minimum 2GB
✓ Miejsce na dysku: ~100MB
```

### Instalacja - Sposób 1: Uruchomienie z kodem źródłowym

1. **Zainstaluj Godot Engine 4.1**
   ```bash
   # Linux (przykład dla Ubuntu)
   wget https://downloads.tuxfamily.org/godotengine/4.1/Godot_v4.1-stable_linux.x86_64.zip
   unzip Godot_v4.1-stable_linux.x86_64.zip
   
   # Lub pobierz ze strony: https://godotengine.org/download
   ```

2. **Sklonuj repozytorium**
   ```bash
   git clone https://github.com/malelolPK/ai-checkers.git
   cd ai-checkers
   ```

3. **Otwórz projekt w Godot**
   ```bash
   godot --path . --editor
   ```
   
   Lub:
   - Uruchom Godot Engine
   - Kliknij "Import"
   - Wybierz plik `project.godot`

4. **Uruchom grę**
   - Wciśnij `F5` w edytorze Godot
   - Lub kliknij przycisk "Play" (▶)

### Instalacja - Sposób 2: Uruchomienie z plików .pck (eksporty)

1. **Pobierz Godot runtime**
   ```bash
   # Pobierz wersję bez edytora (mniejsza)
   wget https://downloads.tuxfamily.org/godotengine/4.1/Godot_v4.1-stable_linux.x86_64.zip
   ```

2. **Uruchom grę**
   ```bash
   # Podstawowa wersja
   godot --main-pack Warcaby.pck
   
   # Lub z określoną głębokością AI
   godot --main-pack "Warcaby Głębokością 4.pck"
   godot --main-pack "Warcaby Głębokością 5.pck"
   ```

### Konfiguracja głębokości przeszukiwania AI

W pliku `main.gd` znajdź linię wywołującą algorytm AI i zmień parametr `targetDepth`:

```gdscript
# Dla Minimax
var best_move = ai_script_mini_max.findBestMove(
    GlobalVariables.board, 
    5,  # ← Zmień tę wartość (1-7 rekomendowane)
    "black", 
    previousTurnWasAttack, 
    previousPawnAttack
)

# Dla Alpha-Beta (może handle większe wartości)
var best_move = ai_script_alpha_beta.find_best_move(
    GlobalVariables.board, 
    7,  # ← Alpha-Beta radzi sobie z głębokością 6-8
    "black", 
    previousTurnWasAttack, 
    previousPawnAttack
)
```

**Wpływ głębokości:**
- `depth = 3` → AI patrzy 3 ruchy do przodu (szybkie, słabe)
- `depth = 5` → AI patrzy 5 ruchów do przodu (zbalansowane)
- `depth = 7` → AI patrzy 7 ruchów do przodu (wolne, silne)

---

## 🎮 How to Play

### Zasady gry

1. **Cel gry**: Zbij wszystkie pionki przeciwnika lub zablokuj je, by nie mogły się ruszyć

2. **Ruchy podstawowe**:
   - Pionki poruszają się po przekątnej o jedno pole
   - Białe pionki idą w górę, czarne w dół

3. **Bicia**:
   - Bicie odbywa się przez przeskoczenie pionka przeciwnika
   - Bicie jest obowiązkowe (gra automatycznie wykrywa)
   - Możliwe są bicia wielokrotne w jednej turze

4. **Damki (Kings)**:
   - Pionek staje się damką po dotarciu na koniec planszy
   - Damka może poruszać się we wszystkich kierunkach po przekątnej
   - Damka może przeskakiwać wiele pól

### Sterowanie

- **Lewy przycisk myszy** - wybór pionka i wykonanie ruchu
- Możliwe ruchy są automatycznie podświetlane
- Gra informuje o dostępnych biciach

### Przebieg rozgrywki

**Ruch gracza - wybór pionka i wykonanie ruchu:**

![Rozgrywka - ruch gracza z podświetlonymi możliwościami](./asset/gameplay_player.gif)

**Odpowiedź AI - algorytm oblicza i wykonuje optymalny ruch:**

![Rozgrywka - ruch AI](./asset/gameplay_ai.gif)

---

## 📸 Screenshots & Assets Instructions

### 📁 Gdzie stworzyć folder assets

Utwórz folder w głównym katalogu projektu:

```bash
cd ai-checkers
mkdir -p assets
```

### 🎥 GIF-y do nagrania - WYMAGANE

Musisz nagrać **2 GIF-y** pokazujące rozgrywkę:

#### 1. **`gameplay_player.gif`** - Ruch gracza
**Co pokazać:**
- Kliknięcie w pionek gracza (biały)
- Podświetlenie możliwych ruchów
- Wykonanie ruchu

**Jak nagrać:**
1. Uruchom grę i rozpocznij rozgrywkę
2. Rozpocznij nagrywanie ekranu (tylko obszar planszy + panel info)
3. Kliknij na swojego pionka (białego)
4. Poczekaj chwilę żeby widać było podświetlone ruchy
5. Wykonaj ruch
6. Zatrzymaj nagranie
7. Zapisz jako `assets/gameplay_player.gif`

**Parametry:**
- Długość: 3-5 sekund
- Rozmiar: max 5MB
- FPS: 15-20 (wystarczy)

#### 2. **`gameplay_ai.gif`** - Ruch AI
**Co pokazać:**
- Tura AI (komputer myśli)
- Wykonanie ruchu przez AI (czarny pionek)
- Zmiana tury z powrotem na gracza

**Jak nagrać:**
1. Po swoim ruchu czekaj na ruch AI
2. Rozpocznij nagrywanie PRZED ruchem AI
3. Nagraj jak AI wykonuje ruch
4. Zatrzymaj nagranie gdy tura wróci do gracza
5. Zapisz jako `assets/gameplay_ai.gif`

**Parametry:**
- Długość: 2-4 sekundy
- Rozmiar: max 5MB
- FPS: 15-20

### 🛠️ Narzędzia do nagrywania (Linux)

```bash
# Peek - najlepsze do GIF-ów (REKOMENDOWANE)
sudo apt install peek

# SimpleScreenRecorder (nagrywa MP4, potem konwertuj na GIF)
sudo apt install simplescreenrecorder

# Konwersja MP4 → GIF (jeśli używasz SimpleScreenRecorder)
ffmpeg -i input.mp4 -vf "fps=15,scale=800:-1:flags=lanczos" -c:v gif output.gif
```

### 📐 Format GIF-ów w README

Już dodane w odpowiednich sekcjach:

```markdown
![Rozgrywka - ruch gracza](./assets/gameplay_player.gif)
![Rozgrywka - ruch AI](./assets/gameplay_ai.gif)
```

### 📂 Struktura po dodaniu GIF-ów:

```
ai-checkers/
├── README.md
├── assets/
│   ├── gameplay_player.gif  ← WYMAGANE
│   └── gameplay_ai.gif      ← WYMAGANE
├── asset/ (folder z kodem)
└── ...
```

---

## 🔬 Algorithm Comparison

| Aspekt | Minimax | Alpha-Beta Pruning |
|--------|---------|-------------------|
| **Złożoność czasowa** | O(b^d) | O(b^(d/2)) w najlepszym przypadku |
| **Pamięć** | Liniowa względem d | Liniowa względem d |
| **Optymalizacja** | Brak | Przycina drzewo |
| **Głębokość (praktyczna)** | 4-5 poziomów | 6-8 poziomów |
| **Czas obliczeń (d=5)** | ~2-5 sekund | ~0.5-1 sekunda |
| **Jakość ruchów** | Identyczna | Identyczna |

*gdzie: b = branching factor (średnio ~7 ruchów), d = depth (głębokość)*

### Przykład przeszukiwania

**Drzewo dla pojedynczego ruchu (uproszczone):**

```
                      [Pozycja początkowa]
                              │
        ┌────────────┬────────┼────────┬────────────┐
        ▼            ▼        ▼        ▼            ▼
     [Ruch A]    [Ruch B] [Ruch C] [Ruch D]    [Ruch E]
        │            │        │        │            │
    ┌───┼───┐    ┌──┼──┐  ┌──┼──┐  ┌──┼──┐     ┌──┼──┐
    ▼   ▼   ▼    ▼  ▼  ▼  ▼  ▼  ▼  ▼  ▼  ▼     ▼  ▼  ▼
   ...Depth 2...

   🔴 Minimax: Sprawdza WSZYSTKIE gałęzie
   🟢 Alpha-Beta: Przycina nieperspektywiczne gałęzie (zaznaczone X)
```

---

## 🎓 Learning Resources

Jeśli chcesz zrozumieć algorytmy użyte w projekcie:

### Minimax Algorithm
- 📹 [Minimax Algorithm in Game Theory](https://www.youtube.com/watch?v=l-hh51ncgDI)
- 📚 [Minimax - Wikipedia](https://en.wikipedia.org/wiki/Minimax)

### Alpha-Beta Pruning
- 📹 [Alpha-Beta Pruning - MIT OpenCourseWare](https://www.youtube.com/watch?v=xBXHtz4Gbdo)
- 📚 [Alpha-Beta Pruning - Wikipedia](https://en.wikipedia.org/wiki/Alpha%E2%80%93beta_pruning)

### Godot Engine
- 📖 [Godot Official Documentation](https://docs.godotengine.org/en/stable/)
- 📹 [GDScript Tutorial](https://www.youtube.com/watch?v=KjX5llYZ5eQ)

### Game AI
- 📚 Książka: "Artificial Intelligence: A Modern Approach" - Russell & Norvig
- 📚 Książka: "Programming Game AI by Example" - Mat Buckland

---

## 🚧 Future Improvements

### Planowane funkcje

- [ ] **Multiplayer online** - gra przez sieć
- [ ] **Tryb PvP lokalny** - dwóch graczy na jednym komputerze
- [ ] **System trudności** - Easy/Medium/Hard (depth 3/5/7)
- [ ] **Historia ruchów** - cofanie i powtarzanie ruchów
- [ ] **Różne warianty warcabów**:
  - [ ] Warcaby polskie (aktualna wersja)
  - [ ] Warcaby angielskie
  - [ ] Warcaby brazylijskie
  - [ ] Damka 100-polowa

### Optymalizacje techniczne

- [ ] **Memoizacja w AI** - cache już obliczonych pozycji (transposition table)
- [ ] **Iterative Deepening** - progresywne zwiększanie głębokości
- [ ] **Move Ordering** - sortowanie ruchów dla lepszego pruningu
- [ ] **Parallel Search** - wykorzystanie wielu wątków CPU
- [ ] **Neural Network AI** - wykorzystanie uczenia maszynowego
- [ ] **Opening Book** - baza danych otwarć

### UI/UX Improvements

- [ ] **Animacje smooth** - płynniejsze przejścia pionków
- [ ] **Motyw ciemny/jasny**
- [ ] **Różne style plansz** - drewniana, marmurowa, etc.
- [ ] **Statystyki** - liczba wygranych, współczynnik zbić, etc.
- [ ] **Tutorial interaktywny** - nauka zasad w grze
- [ ] **Replay system** - odtwarzanie partii

---

## 🤝 Contributing

Projekt jest otwarty na kontrybucje! Jeśli chcesz pomóc:

1. **Fork** repozytorium
2. Stwórz branch dla nowej funkcji: `git checkout -b feature/AmazingFeature`
3. Commit zmian: `git commit -m 'Add some AmazingFeature'`
4. Push do brancha: `git push origin feature/AmazingFeature`
5. Otwórz **Pull Request**

### Obszary gdzie potrzebna pomoc:

- 🐛 Znajdowanie i naprawianie bugów
- 🎨 Projektowanie UI/UX
- 🧠 Optymalizacja algorytmów AI
- 📝 Dokumentacja i tutoriale
- 🌍 Tłumaczenia (obecnie tylko polski)

---

## 📄 License

Ten projekt jest dostępny na licencji **MIT License**.

```
MIT License

Copyright (c) 2024 [Twoje Imię/Nick]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

**Co to oznacza:**
- ✅ Wolność użycia komercyjnego
- ✅ Modyfikacja i dystrybucja
- ✅ Użycie prywatne
- ❗ Brak gwarancji
- ❗ Autor nie ponosi odpowiedzialności

---

## 👤 Author

**GitHub**: [@malelolPK](https://github.com/malelolPK)

### Kontakt
- 📧 Email: [twój-email@example.com]
- 💼 LinkedIn: [Twój profil LinkedIn]
- 🌐 Portfolio: [twoja-strona.com]

---

## 🙏 Acknowledgments

- **Godot Engine** - za fantastyczny open-source game engine
- **Społeczność Godot** - za wsparcie i tutoriale
- **Claude Shannon** - pionier teorii gier komputerowych
- **John von Neumann** - twórca teorii gier

---

## 📊 Project Stats

```
Linie kodu:      ~2,500+
Języki:          GDScript (100%)
Pliki:           50+
Commity:         [zaktualizuj po pierwszym commicie]
Czas rozwoju:    [podaj czas]
Wersja:          1.0.0
```

---

## 🔗 Related Projects

Jeśli podobał Ci się ten projekt, sprawdź również:

- [Face Expression Recognition VIT](../Face_Expression_recognition_VIT/) - rozpoznawanie emocji z twarzy
- [Fully Connected Layers and CNN From Scratch](../FullyConnectedLayersAndCNNFromScratch/) - implementacja sieci neuronowych od podstaw

---

<div align="center">

### ⭐ Jeśli projekt Ci się podoba, zostaw gwiazdkę na GitHubie! ⭐

**Made with ❤️ and ☕ by [Twoje Imię]**

</div>

---

## 📝 Changelog

### Version 1.0.0 (2024-12-05)
- ✨ Pierwsza pełna wersja gry
- 🤖 Implementacja Minimax i Alpha-Beta
- 🎮 Pełna mechanika warcabów
- 🎨 System menu i UI
- 🔊 Efekty dźwiękowe
- 📦 Eksport do .pck files

---

*README ostatnio zaktualizowane: 5 grudnia 2024*
