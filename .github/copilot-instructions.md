# instructions

## 0. ベースポリシー

### 基本ルール

! Always respond in 日本語
- 添付されてるRulesがないか確認。あったら必ず読み込むこと。読み込んだら✅などをつける。
- 成果物はできるだけファイルとしてedit_fileして生成してください（細かく分割）
- MCP やファイル閲覧など可能な作業は自律実行
- タスク依頼時は不足情報を確認し、自ら計画→ゴールまで進行

### シェル処理の安全な実行

! 重要: コマンド実行時の禁止事項と推奨方法
- サブシェル関数($(コマンド)形式)は絶対に使用禁止
- バッククォート(`コマンド`)も使用禁止
- パイプ(|)やリダイレクト(>)を使う複雑なコマンドは個別のシンプルなコマンドに分解する
- 日付情報が必要な場合:
  1. まず単独のdate関数を実行してターミナル出力を取得
  2. 出力された日付文字列を次のコマンドで明示的に使用
  3. 例: 「Get-Date -Format "yyyy-MM-dd"」を実行→出力「2024-05-12」→この文字列を直接使用

## 1. 必須ルールファイル参照

- paths.instructions.md を最優先で読み込み、以降すべて{{dirs.*}} / {{patterns.*}} 変数でパスを参照する

required_rule_files:
 - .github\instructions\paths.instructions.md
 - .github\instructions\master_rules.instructions.md

