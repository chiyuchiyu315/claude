# Claude Code サブエージェントチーム

Claude Codeの「サブエージェント」機能用の定義ファイル集です。ソフトウェア開発チーム(6体)とインフラエンジニアチーム(6体)、計12体を収録しています。

## チーム構成

### ソフトウェア開発チーム

| ファイル | 役割 | モデル |
|---|---|---|
| `agents/planner.md` | 実装計画の立案(設計・タスク分解) | opus |
| `agents/implementer.md` | 実際のコード実装 | sonnet |
| `agents/code-reviewer.md` | コードレビュー | opus |
| `agents/test-engineer.md` | テストの作成・実行 | sonnet |
| `agents/debugger.md` | バグの根本原因調査・修正 | opus |
| `agents/docs-writer.md` | ドキュメント作成・更新 | sonnet |

### インフラエンジニアチーム

| ファイル | 役割 | モデル |
|---|---|---|
| `agents/infra-architect.md` | インフラ構成の設計 | opus |
| `agents/iac-engineer.md` | Infrastructure as Codeの実装(Terraform等) | sonnet |
| `agents/cicd-engineer.md` | CI/CDパイプラインの構築・修正 | sonnet |
| `agents/sre.md` | 障害対応・運用信頼性(SRE) | opus |
| `agents/infra-security-reviewer.md` | インフラ変更のセキュリティレビュー | opus |
| `agents/cost-optimizer.md` | クラウドコストの分析・削減提案 | sonnet |

## インストール方法

このリポジトリをプロジェクトのルートにcloneし、`agents/` フォルダの中身を `.claude/agents/` にコピー(または `agents/` フォルダ自体を `.claude/agents` にリネーム)してください。

```
git clone <このリポジトリのURL>
cd <リポジトリ名>
mkdir -p .claude
cp -r agents .claude/agents
```

全プロジェクトで共通に使いたい場合は、`~/.claude/agents/` に同様にコピーしてください。

配置後、Claude Codeを(初回のみ)再起動すると、12体のサブエージェントが自動的に認識されます。

## 複数端末での利用

このリポジトリをGitHub等にpushしておけば、別の端末でも `git clone`(または既にcloneしている場合は `git pull`)するだけで最新のエージェント定義を取得できます。

```
git pull
cp -r agents/. .claude/agents/
```

## カスタマイズ

各 `.md` ファイルの先頭にあるYAMLフロントマター(`tools:` / `model:`)を編集すると、使用可能なツールやモデルを調整できます。詳しくは各ファイルの内容、および [Claude Code公式ドキュメント](https://code.claude.com/docs/en/sub-agents) を参照してください。
