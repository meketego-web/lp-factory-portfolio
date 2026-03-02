# LP Factory — 標準作業手順書

## 案件フロー

```
1. 案件発見 (5分)
   └→ CrowdWorks / ココナラで案件を確認

2. 提案・応募 (Claude: /propose)
   └→ 案件要件を貼り付け → 提案文を自動生成

3. 受注後: ヒアリング (10分)
   └→ requirements-schema.yaml に沿ってクライアントから情報収集
   └→ clients/{date}_{name}/requirements.yaml に記入

4. LP生成 (Claude: /generate-lp)
   └→ requirements.yaml → テンプレートカスタマイズ → dist/ に出力

5. 確認・プレビュー (10分)
   └→ ブラウザでデスクトップ/モバイル表示を確認
   └→ 修正が必要なら指示をClaude Codeに伝える

6. 修正対応 (Claude + 人間: 15分)
   └→ クライアントからのフィードバックを反映
   └→ revisions/ に修正前を保存

7. 納品 (Claude: /package + 人間: 5min)
   └→ ZIP + README を生成
   └→ プラットフォーム経由で納品

合計: 人間 45〜60分 / Claude 15〜20分
```

## 修正ポリシー

- ライトプラン: 修正2回まで無料
- スタンダード: 修正3回まで無料
- 追加修正: +2,000円/回
- 「レイアウトの大幅変更」は修正ではなく追加作業として扱う
