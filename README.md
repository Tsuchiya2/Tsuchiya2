# Tsuchiya Yuji

**Backend Engineer | AI-Driven Development | Ruby on Rails / Go**

## About Me

Ruby on Rails を軸にしたバックエンドエンジニアです。

何かを作るとき、指標を取り違えないことを大事にしています。
Catchup Feed は技術記事のキャッチアップ用ですが、最適化したいのは「配信した記事数」ではなく「理解が定着したか」。そのために記事をラジオ番組に変換して、手が塞がる時間でも耳から入る形にしました。
目的から逆算して、要らない複雑さは削る——そういう設計が好きです。

## Tech Stack

**Backend**

![Ruby](https://img.shields.io/badge/-Ruby-CC342D?style=flat&logo=ruby&logoColor=white)
![Rails](https://img.shields.io/badge/-Rails-CC0000?style=flat&logo=rubyonrails&logoColor=white)
![Go](https://img.shields.io/badge/-Go-00ADD8?style=flat&logo=go&logoColor=white)
![Python](https://img.shields.io/badge/-Python-3776AB?style=flat&logo=python&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/-PostgreSQL-336791?style=flat&logo=postgresql&logoColor=white)
![MySQL](https://img.shields.io/badge/-MySQL-4479A1?style=flat&logo=mysql&logoColor=white)

**Frontend**

![TypeScript](https://img.shields.io/badge/-TypeScript-3178C6?style=flat&logo=typescript&logoColor=white)
![React](https://img.shields.io/badge/-React-61DAFB?style=flat&logo=react&logoColor=black)
![Next.js](https://img.shields.io/badge/-Next.js-000000?style=flat&logo=next.js&logoColor=white)

**Infrastructure / DevOps**

![Docker](https://img.shields.io/badge/-Docker-2496ED?style=flat&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/-GitHub%20Actions-2088FF?style=flat&logo=githubactions&logoColor=white)
![Cloudflare](https://img.shields.io/badge/-Cloudflare-F38020?style=flat&logo=cloudflare&logoColor=white)
![Tailscale](https://img.shields.io/badge/-Tailscale-242424?style=flat&logo=tailscale&logoColor=white)
![Raspberry Pi](https://img.shields.io/badge/-Raspberry%20Pi-A22846?style=flat&logo=raspberrypi&logoColor=white)

**AI / LLM**

![Claude](https://img.shields.io/badge/-Claude-191919?style=flat&logo=anthropic&logoColor=white)
![Gemini](https://img.shields.io/badge/-Gemini-8E75B2?style=flat&logo=googlegemini&logoColor=white)
![Ollama](https://img.shields.io/badge/-Ollama-000000?style=flat&logo=ollama&logoColor=white)
![Groq](https://img.shields.io/badge/-Groq-F55036?style=flat)
![VOICEVOX](https://img.shields.io/badge/-VOICEVOX-41C9B4?style=flat)

---

## Featured Projects

### 1. [Catchup Feed](https://github.com/Tsuchiya2/catchup-feed-backend)

![catchup-feed](./assets/catchup-feed-logo.webp)

**技術情報を毎朝10〜15分のラジオ番組に自動変換して届けるパーソナルポッドキャストシステム（実稼働中）**

RSS・YouTube・ポッドキャストから技術情報を自動収集し、LLMで要約 → 台本生成 → VOICEVOXで音声合成した番組を、毎朝ポッドキャストアプリに配信するシステム。「配信された記事数」ではなく**理解の定着**を最適化目標に据え、育児等で手と目が塞がる細切れ時間でも耳から消化できる形に再設計しました。クイズ生成とspaced repetitionによる学習ループも音声に注入しています。

| 項目 | 内容 |
|------|------|
| **バックエンド** | Go 1.26（単一モジュール、server / worker / radio の3バイナリ構成） |
| **フロントエンド** | Next.js 16 + TypeScript (Strict) + TanStack Query（PWAダッシュボード） |
| **AI / 音声** | 要約: Gemini → Groq → Ollama フォールバック連鎖 / TTS: VOICEVOX / 文字起こし: faster-whisper |
| **インフラ** | Raspberry Pi 5 + M3 Mac（夜間バッチ）+ Cloudflare Tunnel + Tailscale + Vercel |
| **ダッシュボード** | [pulse.catchup-feed.com](https://pulse.catchup-feed.com) |

**技術的なポイント:**

*アーキテクチャ:*
- 単一ユーザーに右サイズした設計（初期版のマイクロサービス・gRPC・Prometheus を意図的に撤去し約3.8万行を削減）
- 縮退許容設計 — 「壊れない」より「壊れても翌日勝手に戻る」（Mac不在→エピソード欠番、無料API全滅→ローカルLLM、TTS障害→当日スキップ）
- 固定費ゼロ運用 — LLMは無料枠→ローカルのフォールバック、ホスティングは自宅Pi 5 + Cloudflare Tunnel
- プライバシー分界 — クラウドAPIに流すのは公開記事のみ、書籍・私的データはローカルLLM（Ollama）に限定

*バックエンド:*
- RSS / YouTube / ポッドキャストのマルチモーダル取り込み + 書籍PDFのRAG取り込み（Python）
- 理解定着の学習ループ — 放送記事からクイズを自動生成し、spaced repetition（3段ラダー）で復習を翌朝の番組に注入
- トークン認証付きプライベートRSS配信（友人への限定配信、平文トークン非保存・404統一応答）
- セキュリティ実装 — HttpOnly Cookie JWT・SSRF防御・XFF詐称対策のレート制限

*フロントエンド:*
- OpenAPI仕様からの型自動生成によるEnd-to-End型安全性
- ソース管理・友人/トークン管理・アクセスログ・学習トラッカーのPWAダッシュボード

*開発プロセス:*
- Claude Codeのマルチエージェントオーケストレーション（親がタスク分解・裁定、実装エージェントとレビューエージェントを分離）で開発

📦 [フロントエンド リポジトリ](https://github.com/Tsuchiya2/catchup-feed-frontend)

---

### 2. [EDAF - Evaluator-Driven Agent Flow](https://github.com/Tsuchiya2/evaluator-driven-agent-flow)

![EDAF](./assets/edaf-logo.webp)

**AIコード生成の品質を自動評価・保証する7フェーズ開発フレームワーク**

Claude Codeのサブエージェント機能を活用し、**9つの専門エージェント + 40の評価者**による多層的な品質ゲートを実装。AIが生成したコードを自動的に評価・改善するサイクルを構築しました。

| 項目 | 内容 |
|------|------|
| **技術** | Claude Code Subagent, Prompt Engineering |
| **特徴** | 7フェーズ品質ゲート、自己適応型アーキテクチャ（技術スタック自動検出） |
| **対応** | 11言語、50+フレームワーク |
| **実績** | Rails 6.1→8.1 + webpacker→esbuild移行を約1.5時間で完了（196ファイル変更、JSバンドル76%削減） |

**技術的なポイント:**
- 並列評価によるパフォーマンス最適化
- サンドボックス実行による安全なコード評価
- フィードバックループによる自動修正・再評価
- 3,500行以上の設計書を自動生成

📝 [EDAFの解説記事（Qiita）](https://qiita.com/Tsuchiya2/items/013a467c07286c6732f5)
📝 [EDAFでRails 6.1→8.1アップグレード実践記事（Qiita）](https://qiita.com/Tsuchiya2/items/f99f181d998bbbacb4c2)

---

### 3. [ReLINE - 猫メッセンジャーBot](https://github.com/Tsuchiya2/cat_salvages_the_relationship)

![ReLINE](./assets/cat_salvages_the_relationship-logo.webp)

**休眠グループチャットを活性化するLINE Bot**

コロナ禍で連絡が途切れがちなグループに、かわいい猫のマスコットが会話のきっかけを自動配信。LINE Messaging APIを活用したイベント駆動アーキテクチャで実装しました。

| 項目 | 内容 |
|------|------|
| **技術** | Ruby 3.4 + Rails 8.1 + MySQL 8.0 |
| **連携** | LINE Messaging API |
| **テスト** | RSpec + Selenium（88%カバレッジ） |
| **フロント** | Hotwire (Turbo + Stimulus) + Bootstrap 5 |

**技術的なポイント:**
- サービスオブジェクトによる責務分離（Fat Model/Controller回避）
- ストラテジーパターンによる動的イベントハンドラー選択
- Rack::Attackによるレート制限・ブルートフォース対策
- Brakeman・bundler-auditによるセキュリティ監査

---

## Links

[![Qiita](https://img.shields.io/badge/-Qiita-55C500?style=flat&logo=qiita&logoColor=white)](https://qiita.com/Tsuchiya2)
[![X](https://img.shields.io/badge/-X-000000?style=flat&logo=x&logoColor=white)](https://x.com/Tsuchiya2_)
