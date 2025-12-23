# Phase 1 演習問題集

各練習の具体的なコード例と課題です。
順番に進めていきましょう。

---

## 📝 演習1: Hello World

### 目標
基本的なFlutterアプリの構造を理解する

### 手順
```bash
cd phase1_basics_practice
flutter create hello_world
cd hello_world
```

### 完成コード (lib/main.dart)
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Hello World',
      theme: ThemeData(
        colorScheme: ColorScheme.fromSeed(seedColor: Colors.blue),
      ),
      home: const HelloWorldPage(),
    );
  }
}

class HelloWorldPage extends StatelessWidget {
  const HelloWorldPage({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        backgroundColor: Theme.of(context).colorScheme.inversePrimary,
        title: const Text('Hello World App'),
      ),
      body: const Center(
        child: Text(
          'Hello, World!',
          style: TextStyle(fontSize: 32, fontWeight: FontWeight.bold),
        ),
      ),
    );
  }
}
```

### 確認ポイント
- [ ] アプリが起動する
- [ ] 画面中央に「Hello, World!」が表示される
- [ ] AppBarにタイトルが表示される

### 応用課題
- テキストを自分の名前に変える
- 文字色を青にする
- 文字サイズを変える

---

## 📝 演習2: Container

### 目標
Containerの基本プロパティを理解する

### 完成コード (lib/main.dart)
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Container練習',
      home: const ContainerPage(),
    );
  }
}

class ContainerPage extends StatelessWidget {
  const ContainerPage({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Container練習'),
        backgroundColor: Colors.blue,
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            // 基本的なContainer
            Container(
              width: 100,
              height: 100,
              color: Colors.red,
            ),
            const SizedBox(height: 20),

            // paddingを持つContainer
            Container(
              width: 150,
              height: 100,
              color: Colors.blue,
              padding: const EdgeInsets.all(16),
              child: Container(
                color: Colors.yellow,
              ),
            ),
            const SizedBox(height: 20),

            // 装飾されたContainer
            Container(
              width: 200,
              height: 80,
              decoration: BoxDecoration(
                color: Colors.green,
                borderRadius: BorderRadius.circular(16),
                boxShadow: [
                  BoxShadow(
                    color: Colors.black.withOpacity(0.3),
                    blurRadius: 10,
                    offset: const Offset(0, 5),
                  ),
                ],
              ),
              child: const Center(
                child: Text(
                  '角丸・影付き',
                  style: TextStyle(color: Colors.white, fontSize: 18),
                ),
              ),
            ),
          ],
        ),
      ),
    );
  }
}
```

### 確認ポイント
- [ ] 3つのContainerが縦に並んでいる
- [ ] paddingで内側の余白ができている
- [ ] 角丸と影が表示されている

### 応用課題
- 4つ目のContainerを追加
- marginを使って外側の余白を追加
- 異なる色の組み合わせを試す

---

## 📝 演習3: Text

### 完成コード (lib/main.dart)
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Text練習',
      home: const TextPage(),
    );
  }
}

class TextPage extends StatelessWidget {
  const TextPage({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Text練習'),
        backgroundColor: Colors.purple,
      ),
      body: const Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Text('普通のテキスト'),

            Text(
              '大きいテキスト',
              style: TextStyle(fontSize: 32),
            ),

            Text(
              '太字のテキスト',
              style: TextStyle(
                fontSize: 24,
                fontWeight: FontWeight.bold,
              ),
            ),

            Text(
              '赤い斜体テキスト',
              style: TextStyle(
                fontSize: 20,
                color: Colors.red,
                fontStyle: FontStyle.italic,
              ),
            ),

            Text(
              '装飾されたテキスト',
              style: TextStyle(
                fontSize: 28,
                color: Colors.blue,
                fontWeight: FontWeight.bold,
                letterSpacing: 2.0,
                decoration: TextDecoration.underline,
              ),
            ),
          ],
        ),
      ),
    );
  }
}
```

### 確認ポイント
- [ ] 5種類のテキストが表示される
- [ ] それぞれ異なるスタイルになっている

### 応用課題
- 自分の好きな言葉を表示
- グラデーション風の色を複数使う
- 文字間隔を調整

---

## 📝 演習4: Column と Row

### 完成コード (lib/main.dart)
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Column/Row練習',
      home: const ColumnRowPage(),
    );
  }
}

class ColumnRowPage extends StatelessWidget {
  const ColumnRowPage({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Column/Row練習'),
        backgroundColor: Colors.teal,
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            // Row 1
            Row(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                Container(width: 50, height: 50, color: Colors.red),
                const SizedBox(width: 10),
                Container(width: 50, height: 50, color: Colors.green),
                const SizedBox(width: 10),
                Container(width: 50, height: 50, color: Colors.blue),
              ],
            ),
            const SizedBox(height: 20),

            // Row 2
            Row(
              mainAxisAlignment: MainAxisAlignment.spaceAround,
              children: [
                Container(width: 60, height: 60, color: Colors.orange),
                Container(width: 60, height: 60, color: Colors.purple),
                Container(width: 60, height: 60, color: Colors.pink),
              ],
            ),
            const SizedBox(height: 20),

            // Row 3 with different heights
            Row(
              mainAxisAlignment: MainAxisAlignment.center,
              crossAxisAlignment: CrossAxisAlignment.end,
              children: [
                Container(width: 40, height: 100, color: Colors.cyan),
                const SizedBox(width: 10),
                Container(width: 40, height: 70, color: Colors.lime),
                const SizedBox(width: 10),
                Container(width: 40, height: 50, color: Colors.amber),
              ],
            ),
          ],
        ),
      ),
    );
  }
}
```

### 確認ポイント
- [ ] 3行のRowが表示される
- [ ] 各Rowで異なる配置になっている
- [ ] 高さが異なるContainerが下揃えになっている

### 応用課題
- 4×4のグリッドを作る
- mainAxisAlignmentを変えて違いを確認
- crossAxisAlignmentを変えて違いを確認

---

## 📝 演習5: Stack（重ね合わせ）

### 完成コード (lib/main.dart)
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Stack練習',
      home: const StackPage(),
    );
  }
}

class StackPage extends StatelessWidget {
  const StackPage({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Stack練習'),
        backgroundColor: Colors.indigo,
      ),
      body: Center(
        child: Stack(
          alignment: Alignment.center,
          children: [
            Container(
              width: 300,
              height: 300,
              color: Colors.red,
            ),
            Container(
              width: 200,
              height: 200,
              color: Colors.green,
            ),
            Container(
              width: 100,
              height: 100,
              color: Colors.blue,
            ),
            const Text(
              '重ね合わせ',
              style: TextStyle(
                color: Colors.white,
                fontSize: 24,
                fontWeight: FontWeight.bold,
              ),
            ),
          ],
        ),
      ),
    );
  }
}
```

### 確認ポイント
- [ ] 四角形が重なって表示される
- [ ] テキストが最前面に表示される

### 応用課題
- Positionedを使って位置を指定
- 円形のContainerを重ねる
- 透明度を変えて重なりを確認

---

## 📝 演習9: カウンターアプリ（StatefulWidget）

### 完成コード (lib/main.dart)
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'カウンターアプリ',
      theme: ThemeData(
        colorScheme: ColorScheme.fromSeed(seedColor: Colors.blue),
      ),
      home: const CounterPage(),
    );
  }
}

class CounterPage extends StatefulWidget {
  const CounterPage({super.key});

  @override
  State<CounterPage> createState() => _CounterPageState();
}

class _CounterPageState extends State<CounterPage> {
  int _counter = 0;

  void _incrementCounter() {
    setState(() {
      _counter++;
    });
  }

  void _decrementCounter() {
    setState(() {
      _counter--;
    });
  }

  void _resetCounter() {
    setState(() {
      _counter = 0;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        backgroundColor: Theme.of(context).colorScheme.inversePrimary,
        title: const Text('カウンターアプリ'),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            const Text(
              'カウント:',
              style: TextStyle(fontSize: 24),
            ),
            Text(
              '$_counter',
              style: const TextStyle(fontSize: 60, fontWeight: FontWeight.bold),
            ),
            const SizedBox(height: 30),
            Row(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                FloatingActionButton(
                  onPressed: _decrementCounter,
                  backgroundColor: Colors.red,
                  child: const Icon(Icons.remove),
                ),
                const SizedBox(width: 20),
                FloatingActionButton(
                  onPressed: _incrementCounter,
                  backgroundColor: Colors.blue,
                  child: const Icon(Icons.add),
                ),
              ],
            ),
            const SizedBox(height: 20),
            ElevatedButton(
              onPressed: _resetCounter,
              child: const Text('リセット'),
            ),
          ],
        ),
      ),
    );
  }
}
```

### 確認ポイント
- [ ] ボタンを押すと数字が増減する
- [ ] リセットボタンで0に戻る
- [ ] Hot Reloadで状態が保持される

### 応用課題
- 10ずつ増減するボタンを追加
- 偶数・奇数を表示
- マイナスにならないようにする

---

## 🎓 学習の進め方

1. **プロジェクト作成**
   ```bash
   flutter create hello_world
   cd hello_world
   ```

2. **コードを写す**
   - `lib/main.dart`を上記のコードに置き換え

3. **実行**
   ```bash
   flutter run
   ```

4. **動作確認**
   - 意図通りに動くか確認

5. **応用課題**
   - 自分で変更を加えて理解を深める

6. **コミット**
   ```bash
   git add .
   git commit -m "feat(phase1): hello_world - Hello Worldアプリを作成"
   ```

7. **次の演習へ**

---

## 💡 困ったときは

- `.claude/CLAUDE.md` に質問の仕方が載っています
- エラーメッセージをよく読む
- 公式ドキュメントを参照
- 前の演習に戻って復習
