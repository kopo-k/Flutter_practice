# 基本ウィジェット練習 - 写経ガイド

このプロジェクトで基本的なFlutterウィジェットを写経しながら学習します。
各ステップごとにコードを書き写して、`flutter run`で動作を確認してください。

---

## 📝 学習の進め方

1. 各ステップのコードを`lib/main.dart`に写す
2. ファイルを保存（Hot Reloadで即座に反映される）
3. アプリで結果を確認
4. コードの意味を理解する
5. 自分で値を変えて試す

---

## Step 1: Container - 基本的な四角形

### コード
```dart
Container(
  width: 100,
  height: 100,
  color: Colors.red,
),
```

### 学ぶこと
- `Container`: 四角形のボックス
- `width`, `height`: サイズ指定
- `color`: 背景色

### 自分で試そう
- 色を変える: `Colors.blue`, `Colors.green`
- サイズを変える: `width: 200`, `height: 150`

---

## Step 2: Container - パディング（内側の余白）

### コード
```dart
Container(
  width: 200,
  height: 100,
  color: Colors.blue,
  padding: const EdgeInsets.all(16),
  child: Container(
    color: Colors.red,
  ),
),
```

### 学ぶこと
- `padding`: 内側の余白
- `EdgeInsets.all(16)`: 四方向に16の余白
- `child`: 子ウィジェット

### 自分で試そう
- `EdgeInsets.all(32)` - 余白を大きくする
- `EdgeInsets.only(left: 20, top: 10)` - 特定の方向のみ

---

## Step 3: Container - マージン（外側の余白）

### コード
```dart
Column(
  mainAxisAlignment: MainAxisAlignment.center,
  children: [
    Container(
      width: 150,
      height: 50,
      color: Colors.red,
      margin: const EdgeInsets.all(10),
    ),
    Container(
      width: 150,
      height: 50,
      color: Colors.blue,
      margin: const EdgeInsets.all(10),
    ),
    Container(
      width: 150,
      height: 50,
      color: Colors.green,
      margin: const EdgeInsets.all(10),
    ),
  ],
),
```

### 学ぶこと
- `margin`: 外側の余白
- `Column`: 縦に並べる
- `children`: 複数の子ウィジェット

### 自分で試そう
- marginの値を変える
- Containerを追加する

---

## Step 4: Text - 文字を表示

### コード
```dart
Column(
  mainAxisAlignment: MainAxisAlignment.center,
  children: [
    const Text('Hello, Flutter!'),
    const Text(
      'こんにちは',
      style: TextStyle(fontSize: 24),
    ),
    const Text(
      '大きい文字',
      style: TextStyle(
        fontSize: 32,
        fontWeight: FontWeight.bold,
        color: Colors.blue,
      ),
    ),
  ],
),
```

### 学ぶこと
- `Text`: 文字を表示
- `fontSize`: 文字サイズ
- `fontWeight`: 太さ
- `color`: 文字色

### 自分で試そう
- 自分の名前を表示
- 色を変える
- サイズを変える

---

## Step 5: Column - 縦に並べる

### コード
```dart
Column(
  mainAxisAlignment: MainAxisAlignment.center,
  crossAxisAlignment: CrossAxisAlignment.center,
  children: [
    Container(width: 100, height: 50, color: Colors.red),
    Container(width: 150, height: 50, color: Colors.blue),
    Container(width: 120, height: 50, color: Colors.green),
  ],
),
```

### 学ぶこと
- `mainAxisAlignment`: 縦方向の配置
  - `MainAxisAlignment.start` - 上揃え
  - `MainAxisAlignment.center` - 中央揃え
  - `MainAxisAlignment.end` - 下揃え
- `crossAxisAlignment`: 横方向の配置

### 自分で試そう
- `mainAxisAlignment`を変更
- `crossAxisAlignment.start`, `end`を試す

---

## Step 6: Row - 横に並べる

### コード
```dart
Row(
  mainAxisAlignment: MainAxisAlignment.center,
  children: [
    Container(width: 50, height: 100, color: Colors.red),
    Container(width: 50, height: 100, color: Colors.blue),
    Container(width: 50, height: 100, color: Colors.green),
  ],
),
```

### 学ぶこと
- `Row`: 横に並べる
- Columnと同じくmainAxisAlignment/crossAxisAlignmentが使える

### 自分で試そう
- `mainAxisAlignment`を変更
- Containerを追加

---

## Step 7: Column + Row の組み合わせ

### コード
```dart
Column(
  mainAxisAlignment: MainAxisAlignment.center,
  children: [
    Row(
      mainAxisAlignment: MainAxisAlignment.center,
      children: [
        Container(width: 50, height: 50, color: Colors.red),
        Container(width: 50, height: 50, color: Colors.blue),
      ],
    ),
    const SizedBox(height: 20),
    Row(
      mainAxisAlignment: MainAxisAlignment.center,
      children: [
        Container(width: 50, height: 50, color: Colors.green),
        Container(width: 50, height: 50, color: Colors.orange),
      ],
    ),
  ],
),
```

### 学ぶこと
- `SizedBox`: 空白を作る
- ColumnとRowの組み合わせでレイアウトを作る

### 自分で試そう
- 3×3のグリッドを作る
- 色を自由に変える

---

## Step 8: Stack - 重ね合わせ

### コード
```dart
Center(
  child: Stack(
    children: [
      Container(width: 200, height: 200, color: Colors.red),
      Container(width: 150, height: 150, color: Colors.blue),
      Container(width: 100, height: 100, color: Colors.green),
    ],
  ),
),
```

### 学ぶこと
- `Stack`: ウィジェットを重ねる
- 後に書いたものが上に表示される

### 自分で試そう
- 順番を変える
- `Positioned`で位置を指定

---

## Step 9: Image - 画像を表示（ネットワーク画像）

### コード
```dart
Column(
  mainAxisAlignment: MainAxisAlignment.center,
  children: [
    Image.network(
      'https://picsum.photos/200',
      width: 200,
      height: 200,
    ),
    const SizedBox(height: 20),
    const Text('ランダムな画像'),
  ],
),
```

### 学ぶこと
- `Image.network`: ネットワークから画像を読み込む
- `width`, `height`: 画像サイズ

### 自分で試そう
- URLを変える
- サイズを変える

---

## Step 10: 総合演習 - プロフィールカード

### コード
```dart
Center(
  child: Container(
    width: 300,
    padding: const EdgeInsets.all(20),
    decoration: BoxDecoration(
      color: Colors.white,
      borderRadius: BorderRadius.circular(16),
      boxShadow: [
        BoxShadow(
          color: Colors.grey.withOpacity(0.5),
          spreadRadius: 3,
          blurRadius: 7,
          offset: const Offset(0, 3),
        ),
      ],
    ),
    child: Column(
      mainAxisSize: MainAxisSize.min,
      children: [
        Container(
          width: 100,
          height: 100,
          decoration: BoxDecoration(
            color: Colors.blue,
            shape: BoxShape.circle,
          ),
          child: const Icon(
            Icons.person,
            size: 60,
            color: Colors.white,
          ),
        ),
        const SizedBox(height: 16),
        const Text(
          'あなたの名前',
          style: TextStyle(
            fontSize: 24,
            fontWeight: FontWeight.bold,
          ),
        ),
        const SizedBox(height: 8),
        const Text(
          'Flutter初心者',
          style: TextStyle(
            fontSize: 16,
            color: Colors.grey,
          ),
        ),
      ],
    ),
  ),
),
```

### 学ぶこと
- `BoxDecoration`: 装飾（角丸、影など）
- `BorderRadius`: 角丸
- `BoxShadow`: 影
- `Icon`: アイコン表示

### 自分で試そう
- 名前を自分の名前に変える
- 色を変える
- アイコンを変える（`Icons.star`, `Icons.favorite`など）

---

## 🎯 完全なコード例

### main.dart の完全版（Step 10）

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
      title: '基本ウィジェット練習',
      theme: ThemeData(
        colorScheme: ColorScheme.fromSeed(seedColor: Colors.blue),
        scaffoldBackgroundColor: Colors.grey[200],
      ),
      home: const BasicWidgetsPage(),
    );
  }
}

class BasicWidgetsPage extends StatelessWidget {
  const BasicWidgetsPage({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        backgroundColor: Theme.of(context).colorScheme.inversePrimary,
        title: const Text('基本ウィジェット練習'),
      ),
      body: Center(
        child: Container(
          width: 300,
          padding: const EdgeInsets.all(20),
          decoration: BoxDecoration(
            color: Colors.white,
            borderRadius: BorderRadius.circular(16),
            boxShadow: [
              BoxShadow(
                color: Colors.grey.withOpacity(0.5),
                spreadRadius: 3,
                blurRadius: 7,
                offset: const Offset(0, 3),
              ),
            ],
          ),
          child: Column(
            mainAxisSize: MainAxisSize.min,
            children: [
              Container(
                width: 100,
                height: 100,
                decoration: const BoxDecoration(
                  color: Colors.blue,
                  shape: BoxShape.circle,
                ),
                child: const Icon(
                  Icons.person,
                  size: 60,
                  color: Colors.white,
                ),
              ),
              const SizedBox(height: 16),
              const Text(
                'あなたの名前',
                style: TextStyle(
                  fontSize: 24,
                  fontWeight: FontWeight.bold,
                ),
              ),
              const SizedBox(height: 8),
              const Text(
                'Flutter初心者',
                style: TextStyle(
                  fontSize: 16,
                  color: Colors.grey,
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

---

## ✅ チェックリスト

各ステップを完了したらチェック：

- [ ] Step 1: Container基本
- [ ] Step 2: Padding
- [ ] Step 3: Margin
- [ ] Step 4: Text
- [ ] Step 5: Column
- [ ] Step 6: Row
- [ ] Step 7: Column + Row
- [ ] Step 8: Stack
- [ ] Step 9: Image
- [ ] Step 10: プロフィールカード

---

## 💡 学習のコツ

1. **写経する**: まずはそのまま書き写す
2. **保存する**: Hot Reloadで即座に確認
3. **変更する**: 値を変えて動作を確認
4. **理解する**: なぜそうなるか考える
5. **応用する**: 自分なりにアレンジ

---

## 次のステップ

基本ウィジェットをマスターしたら：
- カウンターアプリ（StatefulWidget）に進む
- 状態管理を学ぶ
