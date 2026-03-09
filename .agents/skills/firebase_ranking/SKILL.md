---
name: Firebase Realtime Ranking System
description: Firebase Realtime Databaseを利用した、ゲームスコアのデイリー＆歴代ランキングの実装スキル。
---

# Firebase Realtime Database Ranking System

## 概要
Firebase Realtime Databaseを利用して、ゲームのスコアを「本日（デイリー）」と「歴代（オールタイム）」の2つのタブで表示するランキングシステムの実装パターンです。

## 機能要件
- ユーザー名の入力とローカルストレージへの保存 (`mathris_player_name`, `mathris_player_id`)
- Firebaseの初期化とデータベース参照の作成 (`scores` と `daily_scores/YYYY-MM-DD`)
- 同時接続数を抑えるための、取得・送信時のオンデマンド接続（`goOnline()` / `goOffline()`）
- 自己ベスト更新時のみデータを保存するトランザクション処理
- ランキングの降順ソート、同点時のタイムスタンプ比較（先着順）表示

## 主な実装 (ranking.js)
- `initFirebase(config)`: Firebaseの初期化
- `fetchRankings()`: 歴代・本日のデータを一度だけ取得してUIを更新し、即座にオフラインにする
- `submitScore(score, level)`: データをトランザクションで送信し、自己ベストの場合のみ更新する

## HTML構造
```html
<div class="ranking-tabs">
    <button id="tab-daily" class="tab-btn active">本日</button>
    <button id="tab-alltime" class="tab-btn">歴代</button>
</div>
<ul id="ranking-list-daily" class="ranking-list">...</ul>
<ul id="ranking-list-alltime" class="ranking-list hidden">...</ul>
```
