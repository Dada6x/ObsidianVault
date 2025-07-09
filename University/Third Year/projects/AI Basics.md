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