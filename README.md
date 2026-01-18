# Tsuchiya Yuji

**Backend Engineer | AI-Driven Development | Go / Ruby on Rails**

## About Me

営業職9年を経てエンジニアに転身し、現在はRuby on Railsを中心としたバックエンド開発に従事（2022年4月〜）。

ビジネスサイドとの要件定義から設計・実装・運用まで一貫対応できることが強みです。業務では外部決済企業のエンジニアと連携し、決済機能を実装主担当しました。個人開発ではGo + Clean ArchitectureやAI/LLM活用に取り組み、**実際に稼働するサービス**を複数リリース。開発したcatchup-feedやEDAFは社内でも活用されています。

## Tech Stack

**Backend**

![Ruby](https://img.shields.io/badge/-Ruby-CC342D?style=flat&logo=ruby&logoColor=white)
![Rails](https://img.shields.io/badge/-Rails-CC0000?style=flat&logo=rubyonrails&logoColor=white)
![Go](https://img.shields.io/badge/-Go-00ADD8?style=flat&logo=go&logoColor=white)
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
![Raspberry Pi](https://img.shields.io/badge/-Raspberry%20Pi-A22846?style=flat&logo=raspberrypi&logoColor=white)

**AI / LLM**

![Claude](https://img.shields.io/badge/-Claude-191919?style=flat&logo=anthropic&logoColor=white)
![OpenAI](https://img.shields.io/badge/-OpenAI-412991?style=flat&logo=openai&logoColor=white)

---

## Featured Projects

### 1. [EDAF - Evaluator-Driven Agent Flow](https://github.com/Tsuchiya2/evaluator-driven-agent-flow)

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

### 2. [Catchup Feed](https://github.com/Tsuchiya2/catchup-feed-backend)

![catchup-feed](./assets/catchup-feed-logo.webp)

**AI要約機能を備えたRSS/Atomフィードリーダー（実稼働中）**

技術記事を自動収集し、Claude/OpenAI APIで要約を生成してSlack・Discordへ配信するシステム。バックエンドとフロントエンドを分離したマイクロサービスアーキテクチャで設計し、Raspberry Pi 5で本番運用しています。

| 項目 | 内容 |
|------|------|
| **バックエンド** | Go 1.25 + Clean Architecture |
| **フロントエンド** | Next.js 16 + TypeScript (Strict) + TanStack Query |
| **AI** | Claude Sonnet 4.5 / OpenAI GPT-4o-mini |
| **インフラ** | Raspberry Pi 5 + Cloudflare Tunnel + Vercel |
| **本番URL** | [pulse.catchup-feed.com](https://pulse.catchup-feed.com) |

**技術的なポイント:**

*バックエンド:*
- Clean Architectureによる依存性逆転・テスタビリティの確保
- 並行処理（goroutine）による高速フィード取得
- サーキットブレーカー・レート制限による耐障害性設計
- Prometheusメトリクス・構造化ロギングによる可観測性

*フロントエンド:*
- OpenAPI仕様からの型自動生成によるEnd-to-End型安全性
- Server Components + TanStack Queryによる最適なデータフェッチ
- Vitest + Playwrightによるユニット・E2Eテスト

*インフラ:*
- Cloudflare Tunnelによるポート開放なしのセキュア公開
- GitHub Actionsによる自動テスト・デプロイ

📦 [フロントエンド リポジトリ](https://github.com/Tsuchiya2/catchup-feed-frontend)

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
