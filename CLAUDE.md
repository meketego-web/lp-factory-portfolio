# LP Factory — AI駆動LP制作ファクトリー

## 概要
テンプレートライブラリ × Claude Code Skill で半自動LP制作を行う副業プロジェクト。
1案件あたりの人間作業を60分以内に圧縮する。

## 技術スタック
- HTML / CSS / JS（ビルドツール不要）
- Tailwind CSS CDN（v3系）
- Google Fonts
- バニラJS（フレームワーク不使用）

## ファイル配置ルール

| 出力物 | 保存先 |
|---|---|
| 共通テンプレート | `templates/_base/` |
| 業種テンプレート | `templates/{industry}/` |
| 案件作業フォルダ | `clients/{YYYY-MM-DD}_{client_name}/` |
| 案件要件 | `clients/{date}_{name}/requirements.yaml` |
| 納品物 | `clients/{date}_{name}/dist/` |
| 修正履歴 | `clients/{date}_{name}/revisions/` |
| ポートフォリオ | `portfolio/` |
| 設定 | `config/` |

## 品質基準
- Lighthouse スコア 90+ を目標
- モバイルファーストのレスポンシブデザイン
- セマンティックHTML（適切なheading構造、alt属性）
- CSS変数でカラー・フォントの一括変更が可能であること
- セクション単位でモジュラー構造（コピペで再配置可能）

## テンプレート設計ルール
- Tailwind CDN をHTMLのhead内で読み込む（ビルド不要で納品可能に）
- カスタムスタイルは `<style>` タグ内のCSS変数 + Tailwindユーティリティで管理
- JSは `<script>` タグでページ末尾に記述。外部ライブラリは極力使わない
- 画像はプレースホルダーURL（Unsplash/Pexels）を使用し、クライアントが差替え可能に

## 納品形式
- ZIPファイル（index.html + README.md）
- READMEには: ファイル構成、サーバーへの設置手順、カラー/テキスト変更方法を記載

## 価格設定
- ライトプラン: 10,000円（テンプレートベース、修正2回）
- スタンダード: 15,000円（カスタムレイアウト、修正3回）
- 追加修正: +2,000円/回
- オプション: 追加セクション +3,000円、フォーム設置 +5,000円
