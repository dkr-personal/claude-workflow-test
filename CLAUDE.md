# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Claude Code local installation directory that serves as a wrapper for the official Anthropic Claude Code CLI tool. The project consists of a simple npm package that installs `@anthropic-ai/claude-code` as a dependency and provides a bash script wrapper to execute it.

## Commands

### Running Claude Code
```bash
./claude [command] [options]
```

The `claude` script is a bash wrapper that executes the actual Claude Code CLI from `node_modules/.bin/claude`.

### Package Management
```bash
npm install    # Install dependencies
npm update     # Update Claude Code to latest version
```

## Architecture

This is a minimal wrapper project with the following structure:
- `claude` - Bash script that delegates to the actual Claude Code CLI
- `package.json` - Defines the Claude Code dependency
- `node_modules/@anthropic-ai/claude-code/` - The actual Claude Code implementation

## Workflow Directory Understanding

### spin_spider プロジェクトのワークフロー概要

spin_spiderプロジェクトで実現したい自動化ワークフローシステムの概要：

#### 目的
Claude AIを活用して、GitHub上での開発作業を自動化・効率化する。人間の開発者とAIが協調して高品質なコードを生産する仕組みを構築。

#### 主要なワークフロー

1. **手動制御ワークフロー**
   - `@claude`: クイックな修正・実装
   - `@claude-design`: 設計・分析専用（実装なし）
   - `@claude-review`: 対話形式のコードレビュー

2. **自動対話ワークフロー**
   - `@claude-impl`: 実装ボットがレビューフィードバックを受けて自動改善
   - レビューボットと実装ボットが自動的に対話して品質向上
   - 無限ループ防止や安全機構を備えた自律的な開発

3. **システム管理ワークフロー**
   - OAuthトークンの自動更新
   - プロジェクトファイルのClaude同期

#### 実現したいこと

1. **設計駆動開発**: 大規模な変更は必ず設計フェーズから開始
2. **品質の自動向上**: AIボット同士の対話による反復改善
3. **人間とAIの協調**: 人間が方向性を示し、AIが実装と改善を担当
4. **透明性とトレーサビリティ**: すべてのプロセスがGitHub上で追跡可能

#### 安全性の確保
- 最大対話回数の制限
- クールダウン期間の設定
- 循環パターンの検出
- 適切な権限管理とブランチ戦略
