# apple mx

情報系学生です。
対戦テトリスAI、ゲームAI、探索アルゴリズム、C++高速化、機械学習に興味があります。

## About

ぷよぷよテトリス向けの対戦テトリスAIを開発しています。
限られた思考時間内でより多くの局面を探索し、実戦で強い手を選択することを目標に、探索アルゴリズム・盤面表現・評価関数・機械学習の研究開発を行っています。

特に、bitboard / SIMD を用いた探索最内ループの高速化、beam search による実時間探索、自己対戦ログを用いた評価関数改善、NNUE / AlphaZero 型手法の対戦テトリスAIへの応用に取り組んでいます。

## Main Project

### BEATRIS - 対戦テトリスAI

ぷよぷよテトリス向けの対戦テトリスAIです。
実時間対戦環境で高速に候補手を探索し、強い着手を選択することを目的としています。

BEATRIS本体は現在 private ですが、研究成果の一部として、探索最内ループ高速化のための公開ベンチマークを公開しています。

主な開発内容:

* beam search による実時間探索
* bitboard / SIMD を用いた高速な盤面処理
* 対戦相手の状態を考慮した評価関数
* 自己対戦ログを用いた評価関数改善
* NNUE型の軽量ニューラルネットワークの検証
* AlphaZero型の policy / value network と PUCT 探索の検証

## Public Repository

### TETRIS-BENCH - Tetris AI Benchmark

対戦テトリスAIの探索最内ループ高速化を検証するための C++ ベンチマークプロジェクトです。

Repository:
https://github.com/applemx/TETRIS-BENCH

主な内容:

* 10×24盤面の256bit bitboard表現
* SIMD / bit演算による候補手生成・盤面遷移・特徴量計算
* clys AI実装との比較ベンチマーク
* AVX2 / BMI2 / FMA を用いた低レイヤ最適化
* CMake / Ninja による再現可能なベンチマーク環境

主な成果:

* 探索スループットを既存実装比で約2.03倍に向上
* 特徴量計算を約1.70倍高速化

## Research

### 対戦テトリスAIにおけるbitboardとSIMDを用いた探索最内ループの高速化

対戦テトリスAIでは、候補手生成、盤面遷移、ライン消去、特徴量計算が探索木の各ノードで大量に実行されます。
そのため、探索アルゴリズムだけでなく、盤面表現や実装効率がAIの性能に大きく影響します。

本研究では、10×24盤面を1マス1bitの固定長256bit bitboardとして表現し、ビット演算とSIMDを用いて、候補手生成・盤面遷移・特徴量計算を高速化しました。

これにより、同じ実時間制約下でより多くの局面を探索できるようになり、対戦テトリスAIの判断精度向上につながります。

## Current Work

現在は、手作業で設計した線形評価関数に加えて、自己対戦ログや探索結果を用いた評価関数の改善に取り組んでいます。

具体的には、対戦ログから局面特徴、候補手、選択手、勝敗、生存時間、攻撃量などを収集し、候補手ランキングや評価重みの改善を行っています。

また、将棋AIで使われるNNUE型の軽量ニューラルネットワークや、AlphaZero型の policy / value network、PUCT探索を対戦テトリスAIへ適用し、高速な古典探索と機械学習による評価精度向上を両立できるかを検証しています。

## Publication

* 情報処理学会 研究報告ゲーム情報学（GI）

  * Title: 対戦テトリスAIにおけるbitboardとSIMDを用いた探索最内ループの高速化
  * IPSJ SIG Technical Report: 2026-GI-57, No.13, pp.1-6
  * URL: https://ipsj.ixsq.nii.ac.jp/records/2007480

## Demo / Video

* 研究発表デモ動画
  https://www.youtube.com/watch?v=nx-GnP7SyXc&t=3778s

* YouTube Channel
  https://www.youtube.com/@applemx4071
