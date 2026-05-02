# CLAUDE.md

## プロジェクト概要

タスクボード アプリケーション（task-board2）

---

## デプロイ先

**GitHub Pages:** https://amotoki7.github.io/task-board2/

デプロイ手順:
```
npm run deploy
```
（`predeploy` で自動ビルド → `gh-pages` で `dist/` を `gh-pages` ブランチに公開）

---

## 技術スタック

| 種別 | 技術 |
|---|---|
| UIライブラリ | React 18 |
| ビルドツール | Vite 5 |
| 言語 | JavaScript (JSX) |
| スタイリング | Plain CSS（コンポーネントごとに `.css` ファイルを対応させる） |
| 状態管理 | React `useState` / `useEffect`（外部ライブラリなし） |
| 永続化 | `localStorage` |
| デプロイ | gh-pages |

---

## コンポーネント命名規約

### ファイル名
- コンポーネントファイルは **PascalCase**（例: `TaskItem.jsx`, `AddTaskForm.jsx`）
- 対応するスタイルファイルも同名にする（例: `TaskItem.css`）

### コンポーネント名
- 関数コンポーネントは **PascalCase**（例: `function TaskItem() {}`）
- `export default` で単一エクスポートする

### CSS クラス名
- **kebab-case**（例: `.task-item`, `.add-btn`, `.board-title`）
- 状態を表す修飾クラスは単語のみ（例: `.completed`, `.disabled`）

### 変数・関数名
- 状態変数: **camelCase**（例: `inputValue`, `tasks`）
- イベントハンドラ: `handle` プレフィックス（例: `handleKeyDown`）
- 状態更新関数: 動詞 + 対象（例: `addTask`, `toggleTask`, `deleteTask`）

---

## Git 運用ルール

### 基本方針

**コードを変更するたびに、必ずコミットしてGitHubへプッシュすること。**

### 手順

1. 変更をステージング
   ```
   git add <変更ファイル>
   ```
   (`git add -A` や `git add .` は機密ファイルや意図しないファイルを含む恐れがあるため、ファイル名を明示して追加すること)

2. コミット（変更の目的を簡潔に記述）
   ```
   git commit -m "変更内容の説明"
   ```

3. GitHubへプッシュ
   ```
   git push origin <ブランチ名>
   ```

### コミットメッセージ規則

- 何を変えたかより「なぜ変えたか」を重視する
- 1〜2文で簡潔にまとめる
- 例: `feat: タスクの優先度フィルタを追加`, `fix: 完了タスクが削除できないバグを修正`

### ブランチ運用

- `main` ブランチへの直接プッシュは避け、機能ごとにブランチを切る
- ブランチ名の例: `feature/add-priority-filter`, `fix/delete-task-bug`
- 作業完了後はPRを作成してマージする

### 禁止事項

- `--no-verify` でフックをスキップしない
- `--force` プッシュは明示的な指示がない限り使用しない
- `.env` やシークレットを含むファイルをコミットしない

---

## 開発ガイドライン

- セキュリティ上の脆弱性（SQLインジェクション、XSSなど）を導入しないこと
- コードコメントは「なぜそうしているか」が自明でない場合のみ記述する
- 不要な抽象化や将来の要件を見越した設計はしない
