---
name: pptx-generator
description: python-pptxベースのPPTXスライド生成スキル。「スライドを作って」「プレゼン資料を作成して」「PPTXを生成して」などのリクエストに使用。12種類のテンプレート（表紙、目次、グラフ、テーブル、カードグリッド、タイムライン等）を組み合わせて日本語ビジネス資料を自動生成する。
---

# PPTX Generator

python-pptxを使ったPPTX生成スキル。コードはすべてスキル内に含まれる。

## 実行手順

1. `references/pptx_generator_code.md`を読み込む
2. コード全体をPythonファイルとして保存
3. `SLIDES_TO_USE`と`SLIDE_CONTENT`をユーザー要件に合わせて編集
4. 実行してPPTXを生成

```bash
pip install python-pptx --break-system-packages
python pptx_generator.py
```

## テンプレート一覧（全12種）

| ID | 名前 | データ構造 |
|----|------|-----------|
| 1 | 表紙 | `title, subtitle, credit` |
| 2 | 目次（リスト） | `items[]` |
| 3 | 左グラフ・右テキスト | `categories[], series[], text_items[]` （棒グラフ） |
| 4 | 左テキスト・右グラフ | `categories[], series[], text_items[]` （円グラフ） |
| 5 | 左テーブル・右テキスト | `columns[], rows[][]` |
| 6 | 左テキスト・右グラフ | `categories[], series[], text_items[]` （折れ線） |
| 7 | カードグリッド | `items[]` （1〜4枚） |
| 8 | 左テキスト・右画像 | `text_items[]` |
| 9 | 3ポイント（丸囲み） | `items[3]` |
| 10 | ポイントリスト（コンパクト） | `items[:4]` |
| 11 | ポイントリスト（大） | `items[:3]` |
| 12 | タイムライン | `timeline_items[:4]` |

## データ構造

### 基本
```python
SLIDES_TO_USE = [1, 2, 3, 4, 1]  # テンプレートID順
SLIDE_CONTENT = {
    1: {"title": "タイトル", "subtitle": "サブ", "credit": "会社名"},
    2: {"title": "目次", "items": ["項目1", "項目2"]},
    ...
}
```

### グラフ
```python
"chart_type": "COLUMN_CLUSTERED",  # or "PIE", "LINE"
"categories": ["Q1", "Q2", "Q3", "Q4"],
"series": [{"name": "売上", "values": [100, 120, 140, 160]}]
```

### テーブル
```python
"columns": ["項目", "2024年", "2025年"],
"rows": [["売上", "100億", "120億"]]
```

### タイムライン
```python
"timeline_items": [
    {"year": "2024", "title": "Phase 1", "description": "説明"}
]
```

## 出典

まつにぃ氏「Python1つでPPTXが作成できる方法」
https://note.com/yugen_matuni/n/ndbd3cc5cff90
