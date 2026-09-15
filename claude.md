# CLAUDE.md

このファイルは、本リポジトリでコード生成・修正作業を行うClaude(AIエージェント)向けのガイドです。

## プロジェクト概要

「GREEN MONITOR ESCAPE」は、1980年代の8ビットパソコン（グリーンモニターCRT）を模した、疑似3Dワイヤーフレーム探索型の脱出ゲームです。詳細仕様は [documents/readme.md](documents/readme.md) を参照してください。

## 技術スタック

- **言語**: HTML5, CSS3, JavaScript (ES6+ Native) のみで構成される、一般的な静的WEBアプリです。
- **依存関係**: 外部ライブラリ・外部アセット（画像・音声ファイル）は一切使用しません。
- **グラフィック**: HTML5 Canvas 2D API（`requestAnimationFrame` によるループ描画）
- **オーディオ**: Web Audio API（`OscillatorNode` / `GainNode` / `AudioBufferSourceNode` による効果音のリアルタイム合成）
- **ファイル構成**: `game.html` 1ファイルに HTML / CSS(`<style>`) / JavaScript(`<script>`) がすべて内包されています。ビルドツールやパッケージマネージャは使用していません。

## 開発・動作確認方法

- ビルド不要。[game.html](game.html) をブラウザで直接開くか、簡易HTTPサーバー（例: `python3 -m http.server`）で配信して動作確認してください。
- 外部ネットワークアクセスやCDN読み込みは行わないでください（オフラインで完結する構成を維持すること）。

## コーディング方針

- 新規の画像・音声アセットファイルを追加しないでください。ビジュアル・音響効果はCanvas描画やWeb Audio APIによる生成のみで実装します。
- グリーンモニターCRT風の配色・エフェクト（ネオングリーン、スキャンライン、発光効果など）のトーンを崩さないよう注意してください。
- 状態遷移（`POWER_OFF` → `BOOT_CRT` → `BOOT_TEXT` → `TITLE` → `PLAY` → `CLEAR`）やマップデータ構造など、既存のゲームロジックの設計を尊重して変更してください。
- ドキュメント類（仕様書・設計メモ等）は `documents/` フォルダ配下に作成してください。
