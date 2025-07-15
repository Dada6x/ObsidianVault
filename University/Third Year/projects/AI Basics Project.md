we want to make the battle ships game 

![[Pasted image 20250709163148.png]]


تتألف اللعبة من شبكة (Grid (ذات أبعاد محددة، تمثل كل الشبكة بحرا يحتوي على أسطول سفن مخفية، هدف اللعبة ،والخلايا التي تمثل سفينة)أو جزءمنها(وذلك تحديد مواقع السفن داخل الشبكة،وذلك بتحديد الخلايا التي تمثل بحرا ُ باالستعانة بمجموعة من الدلائل، و قد تعطى بعض  الخلايا كبداية، تحتوي على مياه وأجزاءمعروفةمن سفن

يتم ملء الخاليا وفق القواعد التالية:
- السفن توضع على الرقعة بشكل أفقي أو عمودي فقط. . 
-  لا يسمح لأي سفينة تلمس خرى، لا بشكل مباشر ولا حتى قطريا 
- على يمين الصفوف وأسفلا الاعمدة توجد أرقام تشير إلى عددالخاليا التي تحتوي عل أجزاء من السفن في كل صف أو عمود. عندما يمتلئ الصف أو لهذا الرقم. تماما  العموديجب أن يكون عدد خاليا أجزاءالسفن مساوي لهذا العدد 
- تنتهي اللعبة عندما يتم وضع جميع السفن على الرقعة أي ملء جميع خاليا الشبكة إما بخلايا سفن او خلايا بحر
- 
  
  
  ### تمثيل مدخالت المسألة:
- قم بتمثيل معطيات املسألة )أبعاد الرقعة، عدد خاليا السفن في األسطر واألعمدة، بعين الاعتبار السفن...( باستخدام اسناديات منفصلة، عرف السفن بطريقةمناسبة آخذا أنه أثناء الحل سيتم استخدام خلايا السفن مللءا لرقعةبالتدريج، وأن هناك تمييز في شكل خلية السفينة بحسب موقعها. ,وعير 
  
  
- 
 -2 مثل خاليا الشبكة املحلولة بإسناديات يمكن أن تكون هذه اإلسنادياتمثال عالقة بين رقم السطر و رقم العمود ونوع ً )إما بحر أو سفينة( مولدة بشكل ديناميكي خالل الحل. القوائم فيتمثيل الشبكة. التستخدم أبدا 3 خاليا الحل بشكل ديناميكي خالل يجب أن تكون مولدة آليا لعب اللعبة، ولكن يمكنك إضافة حقائق ثابتة مبدئيا تمثل خاليا الحل في هذا الجزء من الوظيفة، ثم إزالتهامن الكود في القسم الثاني من الوظيفة..

لنفرض أنهلدينارقعةمحلولة، أي أنهلديكمجموعةالحقائق التي تمثل مدخالت املسألة وخاليا الشبكة املحلولة، وتريد التحقق فيما إذاكان هذا الحل هو حلصحيح، أي يحقق جميع شروطاملسألة.


`solved:- check_rule_1, check_rule_2, … check_rule_n.


الحل الذي يستخدم القوائم يعتريغري مقبول عىل الاطلاق


# this is not working but the grid is working

```
  import 'dart:io';

import 'dart:math';

  

const int gridSize = 5;

const String water = '~';

const String hit = 'X';

const String miss = 'O';

  

List<List<String>> createGrid() {

  return List.generate(gridSize, (_) => List.filled(gridSize, water));

}

  

void printGrid(List<List<String>> grid, {bool hideShips = false}) {

  print('  0 1 2 3 4');

  for (int i = 0; i < gridSize; i++) {

    stdout.write('$i ');

    for (int j = 0; j < gridSize; j++) {

      if (hideShips && grid[i][j] == 'S') {

        stdout.write('$water ');

      } else {

        stdout.write('${grid[i][j]} ');

      }

    }

    print('');

  }

}

  

void placeShip(List<List<String>> grid) {

  final rand = Random();

  int x = rand.nextInt(gridSize);

  int y = rand.nextInt(gridSize);

  grid[y][x] = 'S';

}

  

bool fire(List<List<String>> grid, int x, int y) {

  if (grid[y][x] == 'S') {

    grid[y][x] = hit;

    return true;

  } else if (grid[y][x] == water) {

    grid[y][x] = miss;

  }

  return false;

}

  

void main() {

  final playerGrid = createGrid();

  final aiGrid = createGrid();

  

  placeShip(playerGrid);

  placeShip(aiGrid);

  

  print('Welcome to Terminal Battleship!');

  while (true) {

    // Player Turn

    print('\nYour Turn!');

    printGrid(aiGrid, hideShips: true);

    stdout.write('Enter X (0-4): ');

    int x = int.parse(stdin.readLineSync()!);

    stdout.write('Enter Y (0-4): ');

    int y = int.parse(stdin.readLineSync()!);

  

    if (fire(aiGrid, x, y)) {

      print('💥 You hit the enemy ship!');

      printGrid(aiGrid);

      print('🎉 You win!');

      break;

    } else {

      print('💦 Miss!');

    }

  

    // AI Turn

    print('\nEnemy Turn...');

    final rand = Random();

    int aiX = rand.nextInt(gridSize);

    int aiY = rand.nextInt(gridSize);

  

    print('Enemy fired at ($aiX, $aiY)');

    if (fire(playerGrid, aiX, aiY)) {

      print('🔥 Enemy hit your ship!');

      printGrid(playerGrid);

      print('💀 You lose!');

      break;

    } else {

      print('😅 Enemy missed.');

    }

  }

}
```



# **Report on Battleships Puzzle Validation in Prolog**

### **Introduction**

This project implements a Battleships puzzle validator using Prolog. Battleships is a logic game played on a grid where hidden ships must be located based on given clues. The goal of the program is to verify if a proposed ship placement is valid according to the rules of the game.

The validator checks five main rules: ships are within bounds, ships do not overlap, row and column clues match the ship placements, and ships do not touch each other, even diagonally.

---

### **Representation**

- **Ships** are represented as facts `ship(Row, Col, Size, Dir)` where `Row` and `Col` denote the starting cell, `Size` the ship’s length, and `Dir` its orientation (`horizontal` or `vertical`).
    
- **Occupied cells** (cells covered by ships) are generated dynamically based on ship definitions and stored as `occupied(Row, Col)`.
    
- **Row and column clues** indicating how many ship cells each row and column must contain are stored as `row_count(Row, Count)` and `col_count(Col, Count)`.
    

This dynamic fact representation allows flexible updates and queries during the validation process.

---

### **Functionality**

The program consists of several main parts:

1. **Initialization predicates:**
    
    - `set_ships/1`: Takes a list of ships and asserts them dynamically.
        
    - `set_row_counts/1` and `set_col_counts/1`: Set the expected ship counts per row and column.
        
2. **Occupied cells generation:**
    
    - `generate_occupied_cells/0`: Converts ship definitions into a list of occupied cells on the grid.
        
3. **Validation rules:**
    
    - **Rule 1: Ships within grid**  
        Checks that all ships fit entirely inside the 6x6 grid boundaries.
        
    - **Rule 2: No overlapping ships**  
        Ensures no two ships occupy the same grid cell by verifying uniqueness of occupied cells.
        
    - **Rule 3 & 4: Row and column counts**  
        Validates that the number of ship cells in each row and column matches the provided clues.
        
    - **Rule 5: No touching ships**  
        Checks that no two ships touch each other, including diagonally. This involves verifying that for each occupied cell, none of its adjacent neighbors (including diagonals) are occupied by a different ship.
        
4. **Helper predicates:**
    
    - `same_ship/2` determines if two cells belong to the same ship, based on ship position, size, and orientation.
        
    - `neighbor_delta/2` defines all eight neighbor relative positions for adjacency checks.
        
5. **Combined validation:**
    
    - The `solved/0` predicate runs all checks in sequence, failing if any are violated.
        
6. **User interface:**
    
    - The `run/0` predicate triggers cell generation, runs validation, outputs success/failure, and prints the grid with clues and ship parts visually represented.
        

---

### **Code Structure and Design Choices**

- The program relies on **dynamic facts** to maintain current game state during runtime. This facilitates flexible updates and incremental computations.
    
- The grid is represented implicitly through `occupied/2` facts rather than lists or matrices, complying with project guidelines forbidding the use of lists for grid representation.
    
- Validation is modularized into separate rules, each handling one aspect of the puzzle constraints. This improves clarity and maintainability.
    
- The use of `forall/2` predicates allows elegant iteration over rows, columns, and ship lists without explicit looping constructs.
    
- The `print_grid/0` predicate provides a human-readable display of the board, useful for debugging and user feedback.
    

---

### **Testing and Usage**

To use the validator:

1. Define the ships, row counts, and column counts via the `set_ships/1`, `set_row_counts/1`, and `set_col_counts/1` predicates.
    
2. Call `run/0` to validate the current setup.
    
3. The program outputs rule-by-rule validation status and prints the current board state.
    

Example input:

prolog

Copy code

`set_ships([(1,1,2,horizontal),(3,3,3,vertical),(5,6,1,horizontal)]). set_row_counts([2,0,1,1,1,0]). set_col_counts([1,1,2,1,0,1]). run.`

---

### **Conclusion**

This Battleships validator provides a complete and modular solution to verify ship placements on a 6x6 grid according to official puzzle rules. The program architecture cleanly separates data representation, validation logic, and output formatting.

It supports further extensions such as automated puzzle solving, user interaction for guessing, or integration with a Battleships game engine. This design meets the project requirements and demonstrates a solid understanding of Prolog programming and constraint validation techniques.