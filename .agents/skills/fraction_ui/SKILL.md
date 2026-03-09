---
name: Fraction Input UI
description: 分数問題向けの、分子と分母を上下に分けて入力するUIコンポーネントとその制御スキル。
---

# Fraction Input UI

## 概要
分数の問題が出題された際に、通常の1行テキストボックスから「分子」「水平な線」「分母」の2つの入力フィールドに切り替わるUIと、そのフォーカス移動の制御。

## 構造 (HTML/CSS)
Flexbox (`flex-direction: column`) を用いて、上から「分子 `input`」「線 `div`」「分母 `input`」を配置します。

```html
<div id="fraction-input-container" style="display: flex; flex-direction: column; align-items: center; gap: 5px;">
    <input type="text" id="numerator-input" class="fraction-input" placeholder="分子" style="text-align: center;">
    <div style="width: 120px; height: 3px; background-color: white;"></div>
    <input type="text" id="denominator-input" class="fraction-input" placeholder="分母" style="text-align: center;">
</div>
```

## ロジック (JS)
- キーボードの `Enter` キー押下イベントをフックし、分子の入力中であれば分母の `input` へ `focus()` を移動します（`app.js` の `keydown` イベントリスナー）。
- 分母の入力中に `Backspace` を押し、かつ空欄であれば、分子の `input` に `focus()` を戻します。
- 最終的な回答判定時 (`checkMathAnswer()`) には、分子と分母の値を結合（分母が1の場合は分子のみの整数）して、システムが生成した回答文字列（例: `"1/2"`）と比較します。
