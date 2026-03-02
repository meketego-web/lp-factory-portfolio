---
name: generate-lp
description: 要件YAMLからLPを自動生成。「LP作って」「ランディングページ生成」で起動
---

# LP生成 Skill

クライアントの要件（`requirements.yaml`）をもとに、テンプレートをカスタマイズしてLP一式を生成する。

## 入力

ユーザーから以下のいずれかが提供される:
1. `requirements.yaml` ファイルのパス
2. クライアント情報のテキスト（この場合、まず `requirements.yaml` を生成する）

## 手順

### Step 1: 要件の確認と整理

1. `config/requirements-schema.yaml` を読み込み、スキーマを確認する
2. 提供された情報を `requirements.yaml` にマッピングする
3. 足りない情報はデフォルト値を使用し、`<!-- TODO: クライアントに確認 -->` コメントを追加する

### Step 2: テンプレート選択

1. `requirements.yaml` の `business.industry` を確認する
2. 対応するテンプレートを `templates/{industry}/index.html` から読み込む
3. 業種が未対応の場合は、最も近いテンプレートを選択し、ユーザーに確認する

### Step 3: LP生成

1. テンプレートのプレースホルダー（`{{PLACEHOLDER}}`）を requirements の値で置換する
2. カラーテーマを CSS変数で上書きする（`design.primary_color` 等）
3. セクションの表示/非表示を requirements に応じて調整する
4. 画像URLを設定する:
   - `assets` に指定があればそれを使用
   - なければ業種に適したフリー素材URLを選定
5. 生成物を `clients/{YYYY-MM-DD}_{business.name}/dist/index.html` に出力する

### Step 4: 品質チェック

生成後、以下を確認する:
- [ ] HTML構造が正しいか（閉じタグの漏れ等）
- [ ] すべてのプレースホルダーが置換されているか（`{{` が残っていないか）
- [ ] レスポンシブ表示に影響する問題がないか
- [ ] CTAリンクが設定されているか

### Step 5: 出力報告

ユーザーに以下を報告する:
- 生成されたファイルのパス
- 使用したテンプレート
- TODO項目（クライアントに確認が必要な箇所）
- ブラウザでの確認方法（`dist/index.html` を直接開く）

## 注意事項

- 画像は必ず外部URL（Unsplash/Pexels）またはクライアント提供のURLを使用する
- ローカルファイルパスの画像は使わない（納品時に壊れるため）
- テキストは requirements の内容を尊重し、勝手に大幅な改変をしない
- CTA のリンク先が未指定の場合は `#` にして TODO コメントを残す
