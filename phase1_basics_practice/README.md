# Phase 1 基礎練習フォルダ

このフォルダでフェーズ1の学習を進めます。
各練習ごとに独立したFlutterプロジェクトを作成して学習します。

---

## 📁 フォルダ構成

```
phase1_basics_practice/
├── README.md              # このファイル
├── hello_world/           # 練習1: Hello Worldアプリ
├── container_practice/    # 練習2: Containerウィジェット
├── text_practice/         # 練習3: Textウィジェット
├── column_row_practice/   # 練習4: Column/Row レイアウト
├── stack_practice/        # 練習5: Stack（重ね合わせ）
├── image_practice/        # 練習6: 画像表示
├── button_practice/       # 練習7: ボタン
├── stateful_basic/        # 練習8: StatefulWidget基礎
├── counter_app/           # 練習9: カウンターアプリ
└── profile_card/          # 練習10: プロフィールカード総合演習
```

---

## 🎯 学習方法

### 1. 新しいプロジェクトを作成
```bash
cd phase1_basics_practice
flutter create hello_world
cd hello_world
```

### 2. コードを書く
`lib/main.dart` を編集してアプリを作成

### 3. 実行
```bash
flutter run
```

### 4. 学習完了したらコミット
```bash
git add .
git commit -m "feat(phase1): hello_world - Hello Worldアプリを作成"
```

---

## 📚 各練習の内容

### 練習1: Hello World (hello_world)
**学習内容**:
- Flutter プロジェクトの基本構造
- StatelessWidget の使い方
- MaterialApp, Scaffold の理解

**作成するもの**:
画面中央に「Hello, World!」と表示するシンプルなアプリ

---

### 練習2: Container (container_practice)
**学習内容**:
- Container の基本プロパティ
- width, height, color
- padding, margin
- decoration（角丸、影など）

**作成するもの**:
様々なスタイルのContainerを並べて表示

---

### 練習3: Text (text_practice)
**学習内容**:
- Text の基本的な使い方
- TextStyle（サイズ、色、太さ）
- テキストの配置

**作成するもの**:
様々なスタイルのテキストを表示

---

### 練習4: Column/Row (column_row_practice)
**学習内容**:
- Column（縦並び）
- Row（横並び）
- mainAxisAlignment, crossAxisAlignment
- SizedBox で余白

**作成するもの**:
ボックスを縦横に配置したレイアウト

---

### 練習5: Stack (stack_practice)
**学習内容**:
- Stack（重ね合わせレイアウト）
- Positioned（位置指定）
- Alignment

**作成するもの**:
ウィジェットを重ね合わせた表示

---

### 練習6: Image (image_practice)
**学習内容**:
- Image.network（ネットワーク画像）
- Image.asset（ローカル画像）
- サイズ、フィット方法

**作成するもの**:
画像を表示するアプリ

---

### 練習7: Button (button_practice)
**学習内容**:
- ElevatedButton
- TextButton
- IconButton
- FloatingActionButton
- onPressed の使い方

**作成するもの**:
様々なボタンを配置したUI

---

### 練習8: StatefulWidget基礎 (stateful_basic)
**学習内容**:
- StatefulWidget の構造
- State クラス
- setState() の使い方
- ウィジェットライフサイクル

**作成するもの**:
ボタンを押すとテキストが変わるアプリ

---

### 練習9: カウンターアプリ (counter_app)
**学習内容**:
- 状態管理の実践
- 複数のボタンとイベント
- 条件分岐による表示変更

**作成するもの**:
増減・リセット機能付きカウンターアプリ

---

### 練習10: プロフィールカード (profile_card)
**学習内容**:
- これまでの総復習
- 複雑なレイアウトの組み立て
- デザインの装飾

**作成するもの**:
プロフィールカードUI（名前、アイコン、説明文）

---

## ✅ 進捗チェックリスト

- [ ] hello_world
- [ ] container_practice
- [ ] text_practice
- [ ] column_row_practice
- [ ] stack_practice
- [ ] image_practice
- [ ] button_practice
- [ ] stateful_basic
- [ ] counter_app
- [ ] profile_card

---

## 🔄 Git コミットの例

各練習完了時にコミットすることを推奨：

```bash
# 練習1完了
git add phase1_basics_practice/hello_world
git commit -m "feat(phase1): hello_world - Hello Worldアプリを作成

- StatelessWidgetの基本構造を学習
- MaterialApp, Scaffoldの使い方を理解"

# 練習2完了
git add phase1_basics_practice/container_practice
git commit -m "feat(phase1): container_practice - Containerウィジェットの練習

- width, height, colorの使い方
- padding, marginの違いを理解
- BoxDecorationで装飾"
```

---

## 💡 学習のコツ

1. **一つずつ確実に**: 各練習を完全に理解してから次へ
2. **コードを写す**: まずは見本通りに書いてみる
3. **自分で変更**: 色やサイズを変えて動作を確認
4. **コミット**: 学習内容を記録として残す
5. **復習**: わからなくなったら前の練習に戻る

---

## 📖 参考リソース

- [Flutter公式ドキュメント](https://flutter.dev/)
- [Widget カタログ](https://docs.flutter.dev/ui/widgets)
- `.claude/CLAUDE.md` - 質問用ガイド
- `.claude/learning_plan.md` - 全体の学習プラン

---

## 次のステップ

フェーズ1を完了したら：
- フェーズ2: UI開発（レイアウト、リスト、フォーム、ナビゲーション）
- より実践的なアプリ開発へ
