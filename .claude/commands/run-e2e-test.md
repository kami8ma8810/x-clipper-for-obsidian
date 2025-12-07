# X-Clipper E2E テスト実行

Chrome DevTools MCP を使用して、Content Script の抽出ロジックをテストします。

## 前提条件

1. Chrome ブラウザが起動していること
2. Chrome DevTools MCP が接続されていること
3. X（Twitter）にログインしていること（公開ツイートのみなら不要）

## テスト実行手順

以下の手順で E2E テストを実行してください：

### Step 1: テストケースの読み込み

テストケース定義ファイルを読み込んで、実行するテストを確認します。

```
tests/e2e/fixtures/tweet-urls.ts
```

### Step 2: 各テストケースの実行

高優先度のテストケースから順に実行します：

1. **ページ遷移**: `mcp__chrome-devtools__navigate_page` で対象 URL に遷移
2. **読み込み待機**: `mcp__chrome-devtools__wait_for` でツイートの読み込みを待機
3. **スナップショット取得**: `mcp__chrome-devtools__take_snapshot` で DOM 構造を確認
4. **スクリプト実行**: `mcp__chrome-devtools__evaluate_script` で抽出ロジックを実行
5. **結果検証**: 期待値と比較

### Step 3: 結果レポート

各テストケースの結果を以下の形式でレポートします：

- ✅ PASS: 期待通りの結果
- ❌ FAIL: 期待と異なる結果
- ⏭️ SKIP: ツイートが削除されている等でスキップ

## 実行するテストカテゴリ

$ARGUMENTS

引数なしの場合は高優先度のテストのみ実行します。
引数に `all` を指定すると全テストを実行します。
引数に `quote` `thread` `video` 等を指定するとそのカテゴリのみ実行します。

---

上記の手順に従って、E2E テストを開始してください。
テストケース定義ファイルを読み込み、Chrome DevTools MCP を使用してテストを実行します。
