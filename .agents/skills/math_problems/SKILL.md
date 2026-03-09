---
name: Math Problem Generator
description: 割合、分数、小数、図形など多様な算数問題をランダム生成するロジックのスキル。
---

# Math Problem Generator

## 概要
ゲーム内で出題される多様なカテゴリの算数問題をランダムに生成・評価するエンジンです。

## 出題カテゴリ（17種類）
- **割合**: `percentage_val` (割合の計算), `percentage_rate` (パーセントの逆算)
- **分数 (四則演算)**: `fraction_add`, `fraction_sub`, `fraction_mul`, `fraction_div`
- **小数 (四則演算)**: `decimal_add`, `decimal_sub`, `decimal_mul`, `decimal_div`
- **比・方程式**: `ratio` (比の計算), `equation` (一次方程式の穴埋め)
- **文章題**: `speed` (速さ・時間・距離), `circle_area` (円の面積), `volume` (体積)
- **その他**: `average` (平均), `combination` (組み合わせ)

## 実装のポイント (app.js)
- **ヘルパー関数**: 
  - `r(min, max)`: 指定範囲の整数ランダム生成
  - `s(n, d)`: 分数の約分・文字列フォーマット (`n/d`)
  - `fixFloat(num)`: 浮動小数点誤差の修正
- **`generateQuestion()`**: 各種パラメータをランダム設定し、問題文 (`text`) と正答 (`answer`) をオブジェクトとして生成します。
- **数式描画**: MathJax (`window.MathJax.typesetPromise`) を使用して、生成した分数や数式を美しくレンダリングします。
