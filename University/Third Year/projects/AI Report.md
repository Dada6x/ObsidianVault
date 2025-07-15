
لعبة Battleships هي لعبة منطقية تُلعب على شبكة، حيث تكون السفن مخفية ويجب تحديد مواقعها بناءً على أدلة معينة. هدف البرنامج هو التحقق مما إذا كان الترتيب المقترح للسفن صالحًا وفقًا لقواعد اللعبة.

>هذا المشروع  باستخدام لغة برولوغ، وهو مقسم إلى ملفين [[#FirstFile]] و [[#SecondFile]].
# قواعد اللعبة:

## 1. السفن ضمن الحدود

يجب أن تكون كل سفينة داخل شبكة بحجم 6×6 بالكامل. يتحقق البرنامج من أن نقطة بداية السفينة داخل الشبكة، وأن طول السفينة لا يتجاوز حواف الشبكة.

---
## 2. عدم تداخل السفن

لا يمكن لسفينتين أن تشغلا نفس الخلية. يقوم البرنامج بجمع جميع الخلايا المشغولة ويتأكد من عدم وجود تكرار بينها، مما يضمن عدم تداخل السفن.

---
## 3. تطابق عدد خلايا السفن مع الأعداد المعطاة لكل صف وعمود

يجب أن يكون عدد خلايا السفن في كل صف وكل عمود مطابقًا للأعداد المعطاة كأدلة. يحسب البرنامج عدد الخلايا المشغولة في كل صف وعمود ويقارنه مع الأعداد المتوقعة.

---
## 4. عدم لمس السفن لبعضها البعض

لا يمكن للسفن أن تلامس بعضها البعض أفقيًا أو عموديًا أو حتى قطريًا. لكل خلية مشغولة، يتحقق البرنامج من الخلايا المجاورة للتأكد من عدم وجود خلية مشغولة لسفينة مختلفة.

---

## FirstFile

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




## SecondFile