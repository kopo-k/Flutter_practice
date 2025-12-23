# カウンターアプリ - 写経ガイド（StatefulWidget）

StatefulWidget（状態を持つウィジェット）を学びます。
ボタンを押すと数字が増えるカウンターアプリを作成します。

---

## 📝 学習の進め方

1. 各ステップのコードを`lib/main.dart`に写す
2. ファイルを保存（Hot Reloadで即座に反映）
3. アプリで動作確認
4. コードの意味を理解する

---

## Step 1: 基本的なカウンター

### コード全体

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
  // 状態を保持する変数
  int _counter = 0;

  // カウンターを増やす関数
  void _incrementCounter() {
    setState(() {
      _counter++;
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
              'ボタンを押した回数:',
              style: TextStyle(fontSize: 20),
            ),
            Text(
              '$_counter',
              style: const TextStyle(fontSize: 48, fontWeight: FontWeight.bold),
            ),
          ],
        ),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: _incrementCounter,
        child: const Icon(Icons.add),
      ),
    );
  }
}
```

### 学ぶこと

#### StatefulWidget
```dart
class CounterPage extends StatefulWidget {
  const CounterPage({super.key});

  @override
  State<CounterPage> createState() => _CounterPageState();
}
```
- 状態を持つウィジェット
- `createState()`でStateオブジェクトを作成

#### State クラス
```dart
class _CounterPageState extends State<CounterPage> {
  int _counter = 0;  // 状態を保持

  void _incrementCounter() {
    setState(() {      // setState()で状態を更新
      _counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    // UI構築
  }
}
```

#### setState()
```dart
setState(() {
  _counter++;  // この中で状態を変更
});
```
- **setState()を呼ぶと画面が再描画される**
- setState()なしだと画面は更新されない

### 自分で試そう
- ボタンを押して数字が増えることを確認
- Hot Reloadで状態が保持されることを確認
- Hot Restart (Shift+R) で状態がリセットされることを確認

---

## Step 2: カウンターを減らすボタンも追加

### コード（_CounterPageStateの部分のみ）

```dart
class _CounterPageState extends State<CounterPage> {
  int _counter = 0;

  void _incrementCounter() {
    setState(() {
      _counter++;
    });
  }

  // 追加: カウンターを減らす関数
  void _decrementCounter() {
    setState(() {
      _counter--;
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
              style: TextStyle(fontSize: 20),
            ),
            Text(
              '$_counter',
              style: const TextStyle(fontSize: 48, fontWeight: FontWeight.bold),
            ),
            const SizedBox(height: 30),
            // ボタンを横に並べる
            Row(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                FloatingActionButton(
                  onPressed: _decrementCounter,
                  child: const Icon(Icons.remove),
                ),
                const SizedBox(width: 20),
                FloatingActionButton(
                  onPressed: _incrementCounter,
                  child: const Icon(Icons.add),
                ),
              ],
            ),
          ],
        ),
      ),
    );
  }
}
```

### 学ぶこと
- 複数のsetState()関数を作れる
- Rowで横に並べる
- FloatingActionButtonは複数置ける

### 自分で試そう
- マイナスになることを確認
- ボタンの順番を入れ替える

---

## Step 3: リセットボタンを追加

### コード（buildメソッドに追加）

```dart
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
            style: TextStyle(fontSize: 20),
          ),
          Text(
            '$_counter',
            style: const TextStyle(fontSize: 48, fontWeight: FontWeight.bold),
          ),
          const SizedBox(height: 30),
          Row(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              FloatingActionButton(
                onPressed: _decrementCounter,
                child: const Icon(Icons.remove),
              ),
              const SizedBox(width: 20),
              FloatingActionButton(
                onPressed: _incrementCounter,
                child: const Icon(Icons.add),
              ),
            ],
          ),
          const SizedBox(height: 20),
          // リセットボタン追加
          ElevatedButton(
            onPressed: () {
              setState(() {
                _counter = 0;
              });
            },
            child: const Text('リセット'),
          ),
        ],
      ),
    ),
  );
}
```

### 学ぶこと
- `ElevatedButton`: 通常のボタン
- `onPressed`の中に直接setState()を書ける
- 複数の方法で状態を変更できる

---

## Step 4: 偶数・奇数を表示

### コード（buildメソッドを変更）

```dart
@override
Widget build(BuildContext context) {
  // 偶数か奇数かを判定
  String evenOdd = _counter % 2 == 0 ? '偶数' : '奇数';

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
            style: TextStyle(fontSize: 20),
          ),
          Text(
            '$_counter',
            style: const TextStyle(fontSize: 48, fontWeight: FontWeight.bold),
          ),
          // 偶数・奇数を表示
          Text(
            evenOdd,
            style: TextStyle(
              fontSize: 24,
              color: _counter % 2 == 0 ? Colors.blue : Colors.red,
            ),
          ),
          const SizedBox(height: 30),
          Row(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              FloatingActionButton(
                onPressed: _decrementCounter,
                child: const Icon(Icons.remove),
              ),
              const SizedBox(width: 20),
              FloatingActionButton(
                onPressed: _incrementCounter,
                child: const Icon(Icons.add),
              ),
            ],
          ),
          const SizedBox(height: 20),
          ElevatedButton(
            onPressed: () {
              setState(() {
                _counter = 0;
              });
            },
            child: const Text('リセット'),
          ),
        ],
      ),
    ),
  );
}
```

### 学ぶこと
- `_counter % 2 == 0`: 偶数判定
- 三項演算子: `条件 ? 真の値 : 偽の値`
- 状態に応じて色を変える

---

## Step 5: 完全版 - カラフルなカウンター

### 完全なコード

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
    String evenOdd = _counter % 2 == 0 ? '偶数' : '奇数';
    Color counterColor = _counter % 2 == 0 ? Colors.blue : Colors.red;

    return Scaffold(
      appBar: AppBar(
        backgroundColor: Theme.of(context).colorScheme.inversePrimary,
        title: const Text('カウンターアプリ'),
      ),
      body: Container(
        decoration: BoxDecoration(
          gradient: LinearGradient(
            begin: Alignment.topCenter,
            end: Alignment.bottomCenter,
            colors: [Colors.blue.shade100, Colors.white],
          ),
        ),
        child: Center(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              const Text(
                'カウント:',
                style: TextStyle(fontSize: 24, fontWeight: FontWeight.w500),
              ),
              const SizedBox(height: 10),
              Container(
                width: 150,
                height: 150,
                decoration: BoxDecoration(
                  color: counterColor.withOpacity(0.2),
                  shape: BoxShape.circle,
                  border: Border.all(color: counterColor, width: 4),
                ),
                child: Center(
                  child: Text(
                    '$_counter',
                    style: TextStyle(
                      fontSize: 60,
                      fontWeight: FontWeight.bold,
                      color: counterColor,
                    ),
                  ),
                ),
              ),
              const SizedBox(height: 10),
              Text(
                evenOdd,
                style: TextStyle(
                  fontSize: 28,
                  color: counterColor,
                  fontWeight: FontWeight.bold,
                ),
              ),
              const SizedBox(height: 40),
              Row(
                mainAxisAlignment: MainAxisAlignment.center,
                children: [
                  FloatingActionButton(
                    onPressed: _decrementCounter,
                    backgroundColor: Colors.red,
                    child: const Icon(Icons.remove),
                  ),
                  const SizedBox(width: 30),
                  FloatingActionButton(
                    onPressed: _incrementCounter,
                    backgroundColor: Colors.blue,
                    child: const Icon(Icons.add),
                  ),
                ],
              ),
              const SizedBox(height: 20),
              ElevatedButton.icon(
                onPressed: _resetCounter,
                icon: const Icon(Icons.refresh),
                label: const Text('リセット'),
                style: ElevatedButton.styleFrom(
                  padding: const EdgeInsets.symmetric(
                    horizontal: 30,
                    vertical: 15,
                  ),
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }
}
```

### 学ぶこと
- `LinearGradient`: グラデーション背景
- `BoxDecoration`: 円形、ボーダー
- `withOpacity()`: 透明度
- `ElevatedButton.icon`: アイコン付きボタン

### 自分で試そう
- 色を変える
- 背景のグラデーションを変える
- 10ずつ増やすボタンを追加

---

## 🎯 理解度チェック

以下の質問に答えられるか確認：

1. StatelessWidgetとStatefulWidgetの違いは？
2. setState()の役割は？
3. setState()を呼ばないとどうなる？
4. Hot ReloadとHot Restartの違いは？
5. _counter のアンダースコア(_)の意味は？（プライベート変数）

---

## 💡 応用課題

余裕があれば挑戦：

### 課題1: 2つのカウンター
- 赤と青の2つのカウンターを作る
- それぞれ独立してカウントできる

### 課題2: 範囲制限
- 0〜10の範囲でしかカウントできないようにする
- 範囲外になるボタンは無効化

### 課題3: 履歴表示
- カウンターの変更履歴をリストで表示
- 「+1」「-1」などの操作を記録

---

## ✅ チェックリスト

- [ ] Step 1: 基本的なカウンター
- [ ] Step 2: 増減ボタン
- [ ] Step 3: リセットボタン
- [ ] Step 4: 偶数・奇数表示
- [ ] Step 5: カラフルなカウンター
- [ ] 理解度チェック
- [ ] 応用課題（任意）

---

## 次のステップ

カウンターアプリをマスターしたら：
- フェーズ2: UI開発（レイアウト、リスト、フォーム）に進む
- より複雑な状態管理を学ぶ
