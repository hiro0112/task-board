# Task Board プロジェクト

## プロジェクト概要

タスク管理ボードアプリケーション。

## Git 運用ルール

### コード変更時の必須フロー

**コードを変更するたびに、必ずGitHubへプッシュすること。**

```
git add <変更ファイル>
git commit -m "コミットメッセージ"
git push origin <ブランチ名>
```

### コミットメッセージの規則

プレフィックスを必ずつける:

- `feat:` 新機能追加
- `fix:` バグ修正
- `refactor:` リファクタリング
- `style:` スタイル変更（機能に影響しない）
- `docs:` ドキュメント変更
- `test:` テスト追加・修正
- `chore:` ビルド・設定変更

例: `feat: タスクの完了状態をトグルする機能を追加`

### ブランチ戦略

- `main` — 本番相当のブランチ。直接コミット禁止。
- `feature/<機能名>` — 新機能開発用
- `fix/<バグ名>` — バグ修正用

### プッシュのタイミング

以下のいずれかのタイミングで必ずプッシュする:

1. 機能単位の実装が完了したとき
2. 作業セッション終了時
3. Claude Codeによるコード変更後、毎回

### 禁止事項

- `git push --force` は原則禁止（明示的な指示がある場合のみ許可）
- `main` ブランチへの直接プッシュ禁止
- フックのスキップ (`--no-verify`) は禁止

## デプロイ先

- **リポジトリ:** https://github.com/hiro0112/task-board
- **公開URL:** https://hiro0112.github.io/task-board/
- **デプロイ方法:** `main` ブランチへのプッシュで GitHub Actions が自動実行

## 技術スタック

| カテゴリ | 採用技術 |
|---|---|
| UIライブラリ | React 18 |
| ビルドツール | Vite 6 |
| 言語 | JavaScript (JSX) |
| スタイリング | Plain CSS (CSS Modules なし) |
| 状態管理 | React useState / useEffect |
| 永続化 | localStorage |
| ホスティング | GitHub Pages |
| CI/CD | GitHub Actions |

## コンポーネント命名規約

### ファイル名
- コンポーネントファイルは **PascalCase** + `.jsx` 拡張子
  - 例: `TaskItem.jsx`, `TaskList.jsx`, `AddTaskForm.jsx`
- ユーティリティ・フック・定数は **camelCase** + `.js` 拡張子
  - 例: `useLocalStorage.js`, `taskUtils.js`

### コンポーネント名
- ファイル名と一致させる（default export）
  - 例: `export default function TaskItem() {}`

### CSS クラス名
- **kebab-case** を使用
  - 例: `.task-item`, `.add-btn`, `.input-row`
- 状態を表す修飾クラスは短い形容詞
  - 例: `.done`, `.active`, `.disabled`

### 変数・関数名
- 変数・関数: **camelCase**
- イベントハンドラ: `handle` プレフィックス — 例: `handleKeyDown`, `handleSubmit`
- 状態更新関数: 動詞 + 対象 — 例: `addTask`, `toggleTask`, `deleteTask`

## 開発環境セットアップ

```bash
npm install   # 依存関係インストール
npm run dev   # 開発サーバー起動 → http://localhost:5173/
npm run build # 本番ビルド
```
